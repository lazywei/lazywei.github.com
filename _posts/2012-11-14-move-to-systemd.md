---
layout: post
title: "Move to systemd"
description: ""
category: 
tags: [archlinux]
---
{% include JB/setup %}

昨天幫朋友安裝 ArchLinux 的時候才發現，原來從 2012-10-13 開始，Arch 已經預設安裝 systemd 和 systemd-sysvcompat 來取代 sysvinit 及 initsciprts。

參考官方的 [wiki](https://wiki.archlinux.org/index.php/Systemd)﹐這邊簡單紀錄一下更新過程。

首先先從 pacman 安裝 systemd 以及 systemd-sysvcompat

    $ sudo pacman -S systemd systemd-sysvcompat

接者使用 `systemctl enable daemonname` 來啟動原先寫在 `rc.conf` 中的 DAEMONS。

完成後重新啟動電腦，在進入 grub 介面時按 e，會進入編輯介面，接著在有 `linux` 那行加上 `init=/usr/lib/systemd/systemd`，例如：

    linux /boot/vmlinuz-linux root=UUID=978e3e81-8048-4ae1-8a06-aa727458e8ff ro quiet 
    splash init=/usr/lib/systemd/systemd

重啟後執行指令 `$ cat /proc/1/comm`，若顯示 `systemd` 表示 systemd 已經正常啟動。

接著刪除 initscipts 和 sysvinit，完成！
