---
layout: post
title: "Crawl emome bill"
description: ""
category: 
tags: [ruby]
---
{% include JB/setup %}

最近辦了中華電信的學生專案，所以每個月有 5G 的上網流量額度，雖然手機上有裝 3G watchdog 這個 app，但還是會想知道中華電信那邊紀錄的實際流量，因為 emome 整個操作起來很不順手又麻煩，所以就寫了隻程式去爬未出帳的流量使用了。

Emome 沒有推出 api 實在是很不方便的事情，程式寫完後朋友才說原來有 hami 這個東西…

不過還是附上程式碼吧

https://gist.github.com/lazywei/4951270
