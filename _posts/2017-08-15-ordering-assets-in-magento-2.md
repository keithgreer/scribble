---
id: 1006
title: Ordering assets in Magento 2
date: 2017-08-15T13:38:54+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1006
permalink: /ordering-assets-in-magento-2
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
image: /cms/wp-content/uploads/2016/02/magento-generic.png
categories:
  - Code
tags:
  - GIT
  - Magento Code
  - Magento2
  - XML
---
This one will come in useful until Magento 2 sorts itself out.

For some reason, Magento 2 has no way to order assets out of the box. There is now an extension which allows you to set an order attribute in the CSS tags of the layout XML files and layout updates in Admin Panel.

[Github: Mage2 Ordered Assets](https://github.com/quickshiftin/mage2-ordered-assets) by [Quickshiftin](https://quickshiftin.com)

## Example

Before

<pre>&lt;head&gt;
   &lt;css src="css/app.css" /&gt;
&lt;/head&gt;</pre>

After

<pre>&lt;head&gt;
   &lt;css src="css/app.css" order="100" /&gt;
&lt;/head&gt;</pre>