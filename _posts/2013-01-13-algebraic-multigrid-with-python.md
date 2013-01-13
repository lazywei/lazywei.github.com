---
layout: post
title: "Algebraic Multigrid with python"
description: ""
category: 
tags: [archlinux, python, numerical linear algebra]
---
{% include JB/setup %}

這學期修「數值線性代數」的 final project 主題是 Algebraic Multigrid Method，Google 後發現 python 也有寫好的 (pyamg)[http://code.google.com/p/pyamg/] 可以直接拿來用，archlinux 的 AUR 上也有包好的 package，不過版本有點舊
，如果直接從 AUR 裝的話應該會在 build 的時候噴出一堆 error，所以比較建議的方式是直接抓最新版的 source code 來安裝。

首先從 SVN 中拉出最新版

    svn checkout http://pyamg.googlecode.com/svn/trunk/ pyamg-read-only

接著

    cd pyamg-read-only
    python2.7 setup.py build
    (sudo) python2.7 setup.py install

測試是否安裝成功

    python2.7
    >>> import pyamg

Done！

