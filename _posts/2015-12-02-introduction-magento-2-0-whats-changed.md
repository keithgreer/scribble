---
id: 316
title: 'Magento 2.0: An introduction to what has changed'
date: 2015-12-02T13:58:54+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=316
permalink: /introduction-magento-2-0-whats-changed
colour:
  - orange
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
image: /cms/wp-content/uploads/2015/12/magento2-e1449065924928.png
categories:
  - Notes
tags:
  - Magento
  - Magento2
---
At long last Magento 2.0 has finally be released into the wild. These are a few of the reasons merchants and developers should consider moving to [Magento 2](http://magento.com/developers/magento2). 

## Full Page Caching

Magento 2 introduces full page caching into the community edition of Magento. This means that rather than your web server having to do many slow database queries to render pages and pull blocks together it will first checked for a static/cached version of the page being requested. Load times change from 5-10 seconds for non-cached pages to around 1-2 seconds. Awesome. 

## Better Database Performance

Magento 2 comes ready and able to cope with the larger scale websites that often caused problems before. Rather than one single database Magento 2.0 will allow stores to separate their tables into separate databases. For example a single database can have sole responsibility for content pages, products and categories while maintaining a separate database for users to maintain their cart data. This promise much better performance and reduce the time the system waits for queries to be carried out on a single database.

## System Clean out

Magento 2 has been pretty much built from the ground-up this means old legacy code is no longer in the mix and all those old extensions can be cleared out. The new system will not be compatible with old Magento <1.9 extensions and themes, providing an opportunity to properly optimise extensions and rethink implementations when moving to magento 2.0. 

## Magento 2

* * *

I&#8217;ve been specialising in [Magento Northern Ireland](https://keithgreer.uk/ "Magento Northern Ireland") for over six years working for companies all across the UK and Ireland. If you need help with your ecommerce set-up, [let me know](https://keithgreer.uk/contact).