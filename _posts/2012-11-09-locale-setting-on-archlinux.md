---
layout: post
title: "Locale setting on Archlinux"
description: ""
category: Archlinux
tags: [archlinux, locale]
---
{% include JB/setup %}

因應 Arch 對 rc.conf 的重大變更（ref. [Arch Wiki](https://wiki.archlinux.org/index.php/Initscripts/rc.conf#New_configuration_file)）

設定 locale 的方式也有所不同，以往可以直接在 /etc/rc.conf 中設定，但現在設定的方式如下：

* 編輯 `/etc/locale.gen` 確定想要的 locale 沒有被註解（e.g. `zh_TW.UTF-8`）
* 在 terminal 下輸入 `locale-gen` 並執行以產生相對應檔案（可以用 `locale -a` 列出現在的 locales）
* 編輯 `/etc/locale.conf`，新增 `LANG=zh_TW.UTF-8`
* 登出再登入
* 接著可以用這隻 [script](https://github.com/grawity/code/blob/master/os/locale-check) 來檢查是否設定成功
