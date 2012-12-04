---
layout: post
title: "Use vimdiff for git diff"
description: ""
category: 
tags: [git, vim]
---
{% include JB/setup %}

在 terminal 底下看 git diff 的時候其實不太方便，對我來說並沒有太好讀，所以我改成用 vimdiff 來看，因為 vim 還會幫我上色、對比。

指令很簡單：

    git config --global diff.tool vimdiff
    git config --global difftool.prompt false
    git config --global alias.d difftool

這樣輸入 `git d` 的時候就會自動用 vimdiff，不過因為我有用 [oh my zsh](http://blog.lazywei.com/2012/11/21/oh-my-zsh/) 的 git plugin，所以我並沒有用最後一行的 alias，而是直接寫在 `~/.zshrc`

    alias gdt='git difftool'

