---
id: 966
title: 'PHP: str_replace'
date: 2017-05-26T14:47:46+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=966
permalink: /php-str_replace
colour:
  - 'null'
menu:
  - 'null'
intro:
  - ""
alternative_title_area:
  - ""
blog_tag:
  - ""
blog_category:
  - ""
image: /cms/wp-content/uploads/2017/06/php.png
categories:
  - Code
tags:
  - PHP
  - PHP Basics
---
<pre>str_replace($search,$replace,$subject)</pre>

All instances of $search are replaced with $replace in $subject.

<pre>// Will print to screen: "Why is the sky blue?". 
echo str_replace("red","blue","Why is the sky red?")</pre>