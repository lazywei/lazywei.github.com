---
layout: post
title: "archlinux offline installation of packages"
description: ""
category: 
tags: [archlinux]
---
{% include JB/setup %}

有時在沒有網路的情況下想透過 pacman 安裝套件，可以藉由另一台已經有網路存取能力的電腦來達成。

基本上這篇的內容是參考 [ArchWiki](https://wiki.archlinux.org/index.php/Offline_Installation_of_Packages)：

第一步是要更新 package lists，不過因為我平常就有在更新、而且我今天只是想裝一個小套件而已，所以我就跳過這一步了，有需要的可以參考 wiki 上的教學。

接著查詢要安裝套件的相依列表，例如我想安裝 rp-pppoe 則下指令

    sudo pacman -Sp rp-pppoe > ~/rp-pppoe.list

這樣會把所有需要的套件輸出到 `rp-pppoe.list` 中，接下來打開這個列表，找一台可以上網的電腦把列表中的檔案都抓下來。例如我要安裝 rp-pppoe，列表就是

> ftp://linux.cs.nctu.edu.tw/archlinux/core/os/x86_64/rp-pppoe-3.11-1-x86_64.pkg.tar.xz

接著把這些檔案移到沒有網路能力的電腦上（像是用 usb），然後進入放這些檔案的資料夾，像我是放在 `~/rp-pppoe-3.11-1-x86_64/`：

    cd ~/rp-pppoe-3.11-1-x86_64/

進入後要建立一個資料庫檔案給這個套件：

    repo-add rp-pppoe-3.11-1-x86_64.db.tar.xz *.pkg.tar.xz

再來是讓 pacman 知道這個套件資料庫，所以要修改 `/etc/pacman.conf`，在最上面加入：

    [rp-pppoe-3.11-1-x86_64]
    Server = file:///path/to/rp-pppoe-3.11-1-x86_64

現在就可以讓 pacman 去讀這個套件資料庫並且安裝套件了

    sudo pacman -Sy
    sudo pacman -S rp-pppoe

到這裡就完成了！

