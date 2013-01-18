---
layout: post
title: "Datepicker with rails simple form"
description: ""
category: 
tags: [rails]
---
{% include JB/setup %}

一般使用 jQuery 的 datepicker 搭配 simple_form 時，大概會這樣做

    <%= f.label :deadline, "結束日期" %>
    <%= f.text_field :deadline, class:'datetime_picker' %>

不過 [Stackoverflow](http://stackoverflow.com/questions/5007785/how-do-i-write-a-cleaner-date-picker-input-for-simpleform) 有個漂亮的解法：

    # app/inputs/date_picker_input.rb

    class DatePickerInput < SimpleForm::Inputs::StringInput 
      def input                    
        value = object.send(attribute_name) if object.respond_to? attribute_name
        input_html_options[:value] ||= I18n.localize(value) if value.present?
        input_html_classes << "datepicker"

        super # leave StringInput do the real rendering
      end
    end

這樣使用時就只要

    <%= f.input :deadline, :as => :date_picker %>

更乾淨、方便維護，而且也能用 simple_form 的 wrapper。

實務上我把 `I18n.localize(value)` 改成了 `value`，也就是不使用 I18n。
