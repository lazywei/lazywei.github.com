---
layout: post
title: "Bundle install error"
description: ""
category: 
tags: [rails]
---
{% include JB/setup %}

把專案 clone 回 local 的時候，在執行 `bundle install` 時出現了這個錯誤

    Fatal could not parse object '8c11dd........
    Git error: command git reset --hard '8c11dd

    If this error persists you can try removing the cache directory.

結果好像是因為有些 gem 我已經裝過了，然後版本跟 `Gemfile.lock` 中定義的衝突，所以把 `Gemfile.lock` 砍掉重新執行 `bundle install` 即可。

另外還有碰到這個 error

    Could not find gem 'xxx' in git://github.com/xxx.git (at master).
    Source does not contain any versions of 'xxx (>= 0, runtime)'

或類似的 version error，原因是這個 gem 沒有 `.gemspec`，解法是在 `Gemfile` 中指定版本即可。
