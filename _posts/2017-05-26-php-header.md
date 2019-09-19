---
id: 968
title: 'PHP: header'
date: 2017-05-26T14:51:41+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=968
permalink: /php-header
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
<pre>header($string);</pre>

Used to send a raw HTTP header, often used for page redirects.
  
Must be called before any other output is sent.

<pre>// Redirect the request to https://keithgreer.uk
header("Location: https://keithgreer.uk");</pre>

<pre>// Send an error code to the browser, for example a 404
header("HTTP/1.0 404 Not Found");</pre>