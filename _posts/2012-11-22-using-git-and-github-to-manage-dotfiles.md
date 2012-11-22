---
layout: post
title: "Using git and github to manage dotfiles"
description: ""
category: 
tags: [git, linux]
---
{% include JB/setup %}

在 linux 上有很多設定都是寫在某些 dotfile 中（e.g. .vimrc），所以通常只要能把設定檔帶著走，就是某種程度的 portable 了。

這時候可能會先想到 Dropbox，不過其實有更好的方式，就是使用 git + github 來同時達成同步及版本控制的功能。

昨天就花了一個晚上的時間在整理我的 dotfiles，然後再把他們推上 github。可以參考我的 github repo：[dotfiles](https://github.com/lazywei/dotfiles)，裏面也附上了安裝用的腳本 `install.sh`。

基本方法其實就只是建立一個管理用的資料夾 `~/dotfiles` 放這些設定檔（或甚至資料夾也可以），因為像 vim 或 zsh 在吃設定檔的時候並不會管它是不是真的在那、或者只是符號連結，所以可以放心的在家目錄底下 symlink 到 `~/dotfiles` 中的設定檔。

接著再在這個 `~/dotfiles` 中建立 git repo 即可，進階一點的話還可以用 submodule。這樣以後不管走到哪，只要有網路有 git，就能直接 clone 下來然後安裝這些設定檔了！

