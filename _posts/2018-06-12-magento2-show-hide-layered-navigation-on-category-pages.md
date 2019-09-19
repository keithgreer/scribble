---
id: 1211
title: 'Magento2 &#8211; Show/hide layered navigation on category pages'
date: 2018-06-12T09:48:50+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1211
permalink: /magento2-show-hide-layered-navigation-on-category-pages
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
  - Code
tags:
  - Magento Code
  - Magento2
---
Magento Admin Panel > Catalog > Categories

Click into the category you want to update and then expand the &#8220;Design&#8221;. To remove a layered navigation sidebar that appears by default: 

<pre>&lt;referenceContainer name="catalog.leftnav" remove="true"/&gt;</pre>

h/t: [Jamie McCleave](http://jamiemccleave.com/)