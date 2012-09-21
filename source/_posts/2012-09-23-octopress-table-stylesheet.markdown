---
layout: post
title: "Octopress Table Stylesheet"
date: 2012-09-23 19:27
comments: true
categories: Octopress
published: false
---

Octopress has been very cool for the 2 weeks since I began using. 

My first real hiccup is with using table in [this post](/2012/09/21/i-bought-samwize-dot-com-for-99-cents/). Firstly, I have to figure out how to create table in Octopress. After figuring out, the table doesn't get displayed. It's just not working.

<!-- more -->

## Usage ##

The first problem is with understanding how to create table in Octopress. There isn't [documentation](http://octopress.org/docs/) on that. Shortly, I found out that [markdown inline HTML](http://daringfireball.net/projects/markdown/syntax#html) can be used. That means writing:

``` html
<table>
    <tr>
        <td>Column1</td>
        <td>Column2</td>
    </tr>
</table>	
```

However, you need not write HTML. You can do the same using this:

```
| Column1     | Column2      |
| ----------- | ------------ |
| foo         | foo

```

But that still does not work. You will not see the table borders.

## Table Stylesheet ##

If you inspect the generated HTML, the table tags are present. They are not showing because of the stylesheet. This [post in chinese](http://programus.github.com/blog/2012/03/07/add-table-data-css-for-octopress/) provides a way. Translated, it means:

### 1. Add data-table.css ###

Add data-table.css to `source/stylesheets/`.

{% gist 1993032 %}

### 2. Add link to header ###

In `source/_includes/head.html` insert this below the link for screen.css

``` html
<link href="{{ root_url }}/stylesheets/screen.css" media="screen, projection" rel="stylesheet" type="text/css">
<link href="{{ root_url }}/stylesheets/data-table.css" media="screen, projection" rel="stylesheet" type="text/css" />
```

And now the table appears!

PS: I am puzzled why a default table stylesheet is not added to Octopress

 

