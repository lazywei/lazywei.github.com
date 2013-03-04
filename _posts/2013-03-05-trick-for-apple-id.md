---
layout: post
title: "Trick for apple id"
description: ""
category: 
tags: [OSX]
---
{% include JB/setup %}

剛拿到 macbook 的時候，為了下載 xcode 而先在官網上註冊了 apple id，結果要在 appStore 驗證時卻沒卡在信用卡驗證那邊，因為如果不是在 appStore 上註冊 apple id 的話，是沒辦法在信用卡驗證時選擇「無」這個選項的。

無奈我申請的帳號又是我想用的 mail，所以實在不想拿別的 mail 重新申請，更慘的是 apple id 並不提供刪除的功能.....

不過剛剛靈機一動試了一下，發現這個小技巧：

如果你一開始用 abcdefg@gmail.com 申請，那其實你可以用 abc.efg@gmail.com 再申請一個，也就是說這兩個帳號對 apple id 來說是不同的（在 @gmail.com 之前的那部分任意加入「.」），但是這兩個帳號對 gmail 來說卻是同一個！
所以你可以用後者申請，然後用同個信箱收信！

