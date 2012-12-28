---
layout: post
title: "Rails panel"
description: ""
category: 
tags: [rails]
---
{% include JB/setup %}
 
今天看到的一個不錯的工具 [Rails Panel](https://github.com/dejan/rails_panel)

在 Gemfile 中加入

    group :development do
      gem 'meta_request', '0.2.0'
    end

然後安裝 [Chrome extension](https://chrome.google.com/webstore/detail/railspanel/gjpfobpafnhjhbajcjgccbbdofdckggg)

安裝後開啟 Chrome 的開發者介面（ctrl+shift+i），在瀏覽 rails app 時就能使用 rails panel 檢視相關的 log，非常方便，不過好像只支援用 `rails s` 跑起來的 server？因為我用 apache 跑起來的沒反應，也許再研究看看吧！

