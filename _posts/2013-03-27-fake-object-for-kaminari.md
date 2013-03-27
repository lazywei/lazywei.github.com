---
layout: post
title: "Fake object for kaminari"
description: ""
category: 
tags: [rails, ruby]
---
{% include JB/setup %}

[Kaminari](https://github.com/amatsuda/kaminari) is a wonderful pagination gem for rails.

You just need to append `page` to your Model like this:

    @recipes = Recipe.page(1)

and in views:

    <%= paginate @recipes %>

then it will auto generate the pagination.

But somehow I don't want to append that `page` to my Model. And this will cause to the undefine method of `paginate`.

The solution is to make a fake object. Kaminari expects these method `total_pages`, `current_page`, `limit_value`. So we make these for it:

    current_page = 1
    limit_value = 10
    total_pages = 16
    @pagination = Struct.
      new(:recipes, :current_page, :limit_value, :total_pages).
      new(recipes, current_page, limit_value, total_pages)
    
and then same in views:

    <%= paginate @pagination %>

Ref: 
- [Kaminari's source code](https://github.com/amatsuda/kaminari/blob/master/lib/kaminari/helpers/action_view_extension.rb#L18)
- [Stackoverflow](http://stackoverflow.com/questions/6741567/ruby-metaprogramming-dynamic-instance-variable-names)
