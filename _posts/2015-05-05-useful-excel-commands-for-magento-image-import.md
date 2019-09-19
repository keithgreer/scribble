---
id: 194
title: Useful Excel Commands for Magento Image Import
date: 2015-05-05T09:36:51+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=194
permalink: /useful-excel-commands-for-magento-image-import
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
categories:
  - Code
tags:
  - Imports
  - Magento
  - Microsoft Excel
---
Magento image import can be pretty flaky with case and spaces in the filename of images being uploaded.

<pre>=CONCATENATE("/",SUBSTITUTE(LOWER(F2)," ",""))</pre>

The above code will add a &#8220;/&#8221; at the beginning of the file name (CONCATENATE), it will strip out spaces (SUBSTITUTE) and it will make the filename lowercase (LOWER), in this example for the file name in cell F2.

<!--more-->

This will result in a filename like &#8220;B1268 ED100 red 3.JPG&#8221; being provided by the customer in their spreadsheet which could cause all sorts of bother being translated as &#8220;/b1268ed100red3.jpg&#8221; which won&#8217;t cause much bother when importing into Magento.

Of course, after changing the name of the file in the spreadsheet you&#8217;ll need to rename the actual files themselves. This can be easily achieved using something like [Bulk Rename Utility](http://www.bulkrenameutility.co.uk/) which, as the name suggests will allow you to manipulate all the file names in a given directory by stripping out characters and making the filename and extension lowercase.