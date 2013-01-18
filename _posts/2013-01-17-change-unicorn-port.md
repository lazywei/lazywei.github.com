---
layout: post
title: "Change unicorn port"
description: ""
category: 
tags: [rails, linux]
---
{% include JB/setup %}

原本 unicorn 是吃 port 8080，但是因為一些原因要把 listen port 改掉，改法如下：

`vim config/unicorn.rb`
把 `listen 8080` 改成 `listen 8090`（或任意 port，別衝到就好）

接者下 `sudo netstat -tulpn` 列出吃 8080 的 unicorn 的 PID，然後 `sudo kill UNICORN_PID` 把原先的 unicorn 砍掉
最後把相關的 service 重新啟動就行了。

---
P.S. 因為這是為了 gitlab 改的，所以順便附上 gitlab 用的 apache virtualhost setting

    <VirtualHost *:80>
        ServerName gitlab.example.com

        # Point this to your public folder of teambox
        DocumentRoot /home/gitlab/gitlab

        RewriteEngine On

        <Proxy balancer://unicornservers>
            BalancerMember http://127.0.0.1:8090
        </Proxy>

        # Redirect all non-static requests to thin
        RewriteCond %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f
        RewriteRule ^/(.*)$ balancer://unicornservers%{REQUEST_URI} [P,QSA,L]

        ProxyPass / balancer://unicornservers/
        ProxyPassReverse / balancer://unicornservers/
        ProxyPreserveHost on

        <Proxy *>
            Order deny,allow
            Allow from all
        </Proxy>
        # Custom log file locations
        ErrorLog  /var/log/apache2/gitlab_error.log
        CustomLog /var/log/apache2/gitlab_access.log combined
    </VirtualHost>
