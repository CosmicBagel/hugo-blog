---
title: "This isn't really content"
date: 2017-01-30T15:10:00-07:00
description: "Don't look"
topics:
- non-content monday
- very nice meatballs
---

What does hugo do when no meta? It doesn't publish.

How about minimal (just draft=false) still nothing

How about with a title? nothing

But if all it has is a date tag, it'll publish.

This means that draft is true when not stated.

In the offical Hugo documentation it states that the required variables are title, description, date, and taxonomies. When in fact all you need is a date, but it looks kinda silly on the site.

https://gohugo.io/content/front-matter/

Also I finally realized that Blackfriday configuration is talking about the markdown processor for go -_-

Wouldn't have it been better to call it Markdown Processor (aka Blackfriday)?

Also I'm only using yaml as my front matter because VS Code's markdown highlighter seems to like it best.