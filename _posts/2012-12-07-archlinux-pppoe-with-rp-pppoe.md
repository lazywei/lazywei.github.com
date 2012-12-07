---
layout: post
title: "archlinux pppoe with rp-pppoe"
description: ""
category: 
tags: [archlinu, pppoe]
---
{% include JB/setup %}

因為我把家裡的 Hinet VDSL P874 這台數據機改成「硬撥」、「無線」，所以以往在家裡我都是直接接上網路線或是開 wifi 來上網。不過這次回家發現「硬撥」被關掉了，原來是老媽找中華電信來維修的時候被關掉的，無線網路也順便被關掉了，這下我這台筆電就失去上網能力了…

google 了一下 archlinux 的 pppoe 連線方式，wiki 上是寫設定 pppd，但是我怎麼試都沒成功。

後來看到可以直接用 pppoe-setup 卻發現沒裝 rp-pppoe，但是筆電又連不上網路當然無法直接用 pacman 安裝。

解法是先參考[上一篇](http://blog.lazywei.com/2012/12/07/archlinux-offline-installation-of-packages/)提到的離線安裝 rp-pppoe，下指令

    sudo pppoe-setup

接著依序輸入

* pppoe 用戶名稱（ADSL 的帳號）
* 網路介面（預設是 eth0，不更改直接使用即可）
* 需求值（這個我不知道是什麼，我就直接 enter 跳過了）
* DNS（我用 google 的 8.8.8.8 & 8.8.4.4）
* 密碼（ADSL 的密碼）
* 選擇防火牆（因為我只有偶爾在家才會用到 pppoe，平常在宿舍不會用到，所以我直接選 0 了）

接下來只要下指令 `sudo pppoe-start` 就可以連上網了！

