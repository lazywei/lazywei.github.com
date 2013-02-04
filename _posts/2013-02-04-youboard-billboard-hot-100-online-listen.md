---
layout: post
title: "YouBoard - BillBoard Hot 100 online listen"
description: ""
category: 
tags: [rails]
---
{% include JB/setup %}

在網路上看到人家說他用狂聽 Billboard 來練英文聽力，結果怎麼都找不到可以線上聽 Billboard 的網站，於是一時興起就自己寫了一個來。

YouBoard
---
[網址](http://youboard.lazywei.com/)

> 自動把「告示牌百大熱門榜」加入你的 youtube 歌單中，還每週幫你更新喔XD
> 歡迎大家多多使用

---

這個網站是用 Ruby on Rails 寫的， 用到的 gems：`typhoeus` `nokogiri` `youtube_it` `omniauth` `sidekiq` `bootstrap-rails`

原本是 deploy 在 heroku 上，但因為我要跑 sidekiq 所以就放到 linode 上了。

大致上就是到 [Billboard](http://www.billboard.com/charts/hot-100) 抓前百的歌名，然後用 `youtube_it` 去用歌名搜尋、取得該歌曲的 id，然後存到 DB 中。

接著當使用者點選 subscribe 時再去更新 YouTube Playlist，一開始我是用上一篇提到的 YouTube Batch API 來做，因為短時間內發太多 request 會被 Google 擋掉，不過因為 Batch API 不太好掌控，常常有歌曲沒更新到，所以後來就決定換用 Sidekiq 來跑，當使用者 subscribe 後就丟到 sidekiq 給他去更新歌曲。

---

意外的是，居然真的有人在用了，原本只是寫來自己用的。

也許空一點後可以寫一下去抓 KKBOX 排行榜的功能，這樣會更吸引人吧。
