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

後來看到 pppoe-setup 卻發現沒裝 rp-pppoe，但是筆電又連不上網路當然無法直接用 pacman
