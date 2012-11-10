---
layout: post
title: "Login gmail via command line"
description: ""
category: 
tags: [tips, linux]
---
{% include JB/setup %}

今天發現 linode 上的 rails app 寄信有問題，看了一下 log 發現和上次搬到新主機時遇到的問題一樣
> Net::SMTPAuthenticationError 535-5.7.1 Please log in with your web browser and then try again

簡單說就是要從 linode 的主機那先登入過 gmail，這樣才能用他的 smtp 服務，但是 linode 上我沒裝圖形介面，要登入的話一種是透過 command line browser，一種是用 curl，因為我只是需要先登入一次而已，所以就直接用 curl 了，比較方便：

    curl -u username:password --silent "https://mail.google.com/mail/feed/atom" | tr -d '\n' |
    awk -F '<entry>' '{for (i=2; i<=NF; i++) {print $i}}' |
    sed -n "s/<title>\(.*\)<\/title.*name>\(.*\)<\/name>.*/\2 - \1/p"

以上的指令可以列出未讀郵件，換行是方便閱讀、實際上是一整行的指令。

