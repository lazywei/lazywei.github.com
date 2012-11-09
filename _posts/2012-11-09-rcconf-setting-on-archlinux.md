---
layout: post
title: "rc.conf setting on Archlinux"
description: ""
category: 
tags: [archlinux]
---
{% include JB/setup %}


[上篇](/2012/11/09/locale-setting-on-archlinux/) 提到 `rc.conf` 有重大的變更，大多數的設定都被其他的設定檔所取代，現在我的 `rc.conf` 中只有 DAEMONS 了。

這裡稍微紀錄一下我的 `rc.conf`：

    # /etc/rc.conf
    DAEMONS=(@syslog-ng dbus acpid alsa kdm wicd crond)

注意 dbus 要放在 wicd 之前，不然 wicd 會跳出警示說無法連接到 D-Bus。
