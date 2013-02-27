---
layout: post
title: "Build macbook for development"
description: ""
category: 
tags: [Macbook, OSX, rails]
---
{% include JB/setup %}

昨天拿到了 Macbook Pro with Retina，大概摸了一下後，今天就開始著手建置開發環境。

主要重點是 rails 的環境，還有我習慣用的 vim，最後是 zsh。

首先要先去抓 XCode 和 Command line tool for XCode，這兩個從官網上抓下來就可以了

接下來主要的環境建置是參考 Polydice 的 [setup](https://github.com/polydice/setup)

不過我在裝 homebrew 那遇上了一點錯誤，所以只好自己下指令裝：

    ruby <(curl -fsSkL raw.github.com/mxcl/homebrew/go)

接著 rbenv 的地方我也是自己裝（包含 ruby），也順手裝了 Ruby 2（速度真的快很多！）

在裝 ruby 1.9.3-p374 的時候遇上一點問題，要先裝 apple-gcc42 然後再 env CC=gcc，之後才能正常 compile，但是 ruby 2 就不用了。

後面的東西我就用那個 script 去裝了，裡面有幫你裝 MySQL，但是少了一個我覺得蠻重要的步驟，裝完 MySQL 後請執行：

    mysql_secure_installation

這會幫你把基本的安全措施做好。

跑完 script 都沒問題後，就可以裝 zsh 了，可以用 homebrew 來裝：

    brew install zsh
    sudo chsh /usr/local/bin/zsh YOUR_USERNAME

接著把 oh-my-zsh clone 下來，因為我自己管理 dotfiles 的習慣，所以 .zshrc 就用我自己 github 上的了。

不過要注意的是，我用了 oh-my-zsh 的「rbenv」這個 plugin 會造成 rbenv 路徑出錯，所以就捨而不用

再來是 vim，設定檔方面我也是用我自己 github 上的，然後另外裝了 macvim，裝完之後直接用 spotlight 就可以開，不過如果希望能從 terminal 開的話，可以把下載下來的壓縮檔解開，裡面有一個 mvim，把它丟到 /usr/local/bin/ 底下就可以，也可以順便把 vim alias 到 mvim。

最後是 git 的設定，基本的 name, email 設定就不說了，比較需要記錄的是我更改的 core.editor，這可以在 ~/.gitconfig 中更改

    [core]
        editor = mvim -f

差不多到這裡就完成開發環境的建置了！
