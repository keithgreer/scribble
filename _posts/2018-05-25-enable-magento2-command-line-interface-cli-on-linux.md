---
id: 1193
title: Enable Magento2 Command-Line Interface (CLI) on Linux
date: 2018-05-25T10:05:25+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1193
permalink: /enable-magento2-command-line-interface-cli-on-linux
meta_description:
  - ""
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
  - Notes
tags:
  - Bash
  - Command-Line Interface
  - Linux
  - Magento2
  - Ubuntu
---
For both development, ongoing management and scheduled tasks Magento&#8217;s Command Line Interface is able to do it all. 

To enable CLI for Magento to you&#8217;ll need to make sure the file <magento>/bin/magento is executable by the system. 

If you&#8217;re on the server SSH into the root of your Magneto install and run the command 

<pre>chmod +x bin/magento</pre>

If you&#8217;re on desktop simply locate the file in your file explorer, right click and set the &#8220;Allow executing file as program&#8221; checkbox on the Permissions tab.

<img src="http://keithgreer.uk/cms/wp-content/uploads/2018/05/ubuntu-bin-magento-enable.png" alt="" width="859" height="753" class="alignnone size-full wp-image-1194" srcset="https://keithgreer.uk/cms/wp-content/uploads/2018/05/ubuntu-bin-magento-enable.png 859w, https://keithgreer.uk/cms/wp-content/uploads/2018/05/ubuntu-bin-magento-enable-300x263.png 300w, https://keithgreer.uk/cms/wp-content/uploads/2018/05/ubuntu-bin-magento-enable-768x673.png 768w" sizes="(max-width: 859px) 100vw, 859px" />