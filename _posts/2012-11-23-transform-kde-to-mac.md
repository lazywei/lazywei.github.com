---
layout: post
title: "Transform KDE to Mac"
description: ""
category: 
tags: [kde, archlinux]
---
{% include JB/setup %}

剛使用 Archlinux 時我習慣的桌面是 Gnome，後來 Gnome 常常因為不知名原因當掉，在實在是找不到解法的情況下我轉到了 Kde，一用之下驚為天人，Kde 不愧是被稱為最漂亮的桌面，各種設計也很 user friendly，整體用起來就是很順手。

昨天心血來潮，想把 Kde 改得漂亮一點，這裡就紀錄一下變裝的方法。

*Note*: Archlinux / Kde 4.9.3

首先安裝桌面主題 [Tibanna](http://kde-look.org/content/show.php/Tibanna?content=115322)，安裝方式：**系統設定** -> **工作空間外觀與行為** -> **桌面主題** -> **取得新主題** -> 在搜尋的地方輸入 **Tibanna**

接著安裝元件(Widget)樣式 Bespin，直接通過 [AUR](https://aur.archlinux.org/packages/bespin-svn/) 安裝：

    sudo yaourt -S bespin-svn

以及下載給 Bespin 用的主題包 [Leo-like-bespin pack](http://kde-look.org/content/show.php/Leo-like-bespin+pack?content=118823)，並且解壓縮。
接者進入**系統設定** -> **應用程式外觀** -> 元件樣式選擇 **Bespin** 並點選**設定** -> 點 **Import** 並選則剛剛下載的 Leo-like-bespin 主題解壓縮之後的 `leo-like-dark-v2/leo-like-dark-v2.bespin` -> 點 **Load** 並點**確定** -> 點左方的**圖示** -> **取得新主題** -> 搜尋的地方輸入 **leo like icons v8.5**

*我們用的 icons style 是 [Leo-like-icons V8.5](http://kde-look.org/content/show.php/?content=124176)*

都設定好之後點套用。

再來要安裝 Mac like 的啟動器，我選擇 Daisy，可以直接從 [AUR](https://aur.archlinux.org/packages/kdeplasma-applets-daisy/) 安裝：

    sudo yaourt -S kdeplasma-applets-daisy

安裝好後在 Kde 桌面的面板上新增元件即可。

接著要設定 Mac like 的 global menu，這在我們剛剛從 AUR 裝的 Bespin 中就有包含了，先在桌面頂部新增一個面板，接著在上面新增元件 XBar，接著該元件上方就會有如何寫設定檔的文件，文件說 `MainMenu.xml` 這個檔案在 `~/.kde/share/apps/XBar/MainMenu.xml`，不過我怎麼找都找沒有，所以後來直接新增 `~/.kde4/share/apps/XBar` 這個資料夾，並在底下建立
`MainMenu.xml`，這個設定檔的寫法可以參考[文件](http://cloudcity.sourceforge.net/xbar.html)，這邊也附上我自己的設定檔作為參考：

    <menubar>
        <menu label="Desktop">
        </menu>
        <menu label="Terminal">
            <action label="Konsole on ~" exec="konsole"/>
            <action label="Konsole on RoR" exec="konsole --workdir /srv/http/ror/"/>
            <action label="Start Apache and Mysql" exec="konsole -e sudo systemctl start httpd mysqld"/>
        </menu>
        <action label="Edit Menu" exec="gvim $HOME/.kde4/share/apps/XBar/MainMenu.xml"/>
    </menubar>

最後設定視窗裝飾，**系統設定** -> **工作空間外觀與行為** -> **視窗裝飾** -> **取得新主題** -> 在搜尋的地方輸入 **OS X Aurorae**，安裝之後套用即可。

當然如果要仿 Mac 仿得更像的話，還要設定觸控板的手勢，這等我設定好之後再寫吧！
