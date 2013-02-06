---
layout: post
title: "Swap ; and : in vim"
description: ""
category: 
tags: []
---
{% include JB/setup %}

I found this amazing mapping from [Volloric's vimrc](https://github.com/Valloric/dotfiles/blob/master/vim/vimrc.vim#L479)

It's REALLY AMAZING!

    " In normal mode, we use : much more often than ; so lets swap them.
    " WARNING: this will cause any "ordinary" map command without the "nore" prefix
    " that uses ":" to fail. For instance, "map <f2> :w" would fail, since vim will
    " read ":w" as ";w" because of the below remappings. Use "noremap"s in such
    " situations and you'll be fine.
    nnoremap ; :
    nnoremap : ;
    vnoremap ; :
    vnoremap : ;

And you can use `/\vmap.*:` to find out all the mapping should be modified in your vimrc!

The only inconvenience is that you have to change your habit of using ':', lol.
