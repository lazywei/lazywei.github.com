---
layout: post
title: "Play with YouTube batch api"
description: ""
category: 
tags: [web, rails]
---
{% include JB/setup %}

如果你在短時間內發送太多 request 到 YouTube API，會得到 too many request 之類的回應 ，當然也就無法成功操作。

所以 YouTube 提供了 [Batch Processing](https://developers.google.com/youtube/2.0/developers_guide_protocol_batch_processing) 具體來說就是讓你發一個裏面包含許多操作的 request，這樣就只需要發一個 request 而不是跑 loop 發一堆 requests。

而要發送的目標 url 可以在對應的 feed 找到 batch url。例如某張 playlist：

    https://gdata.youtube.com/feeds/api/playlists/8BCDD04DE8F771B2?v=2

可以在裏面找到

    <link rel='http://schemas.google.com/g/2005#batch' type='application/atom+xml' href='https://gdata.youtube.com/feeds/api/playlists/8BCDD04DE8F771B2/batch?v=2'/>

那個 `href` 屬性就是 batch url，request method 一樣是 post。

至於 request content 則是用 [example](https://developers.google.com/youtube/2.0/developers_guide_protocol_batch_processing#Batch_processing_request_example) 的格式，而像 delete 會用到的 id、影片在 playlist 中的 id 等都可以在 feed 中找到。
