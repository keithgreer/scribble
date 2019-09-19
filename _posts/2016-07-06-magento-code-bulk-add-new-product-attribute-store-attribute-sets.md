---
id: 576
title: 'Magento Code: Bulk add a new product attribute to all store attribute sets'
date: 2016-07-06T10:30:56+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=576
permalink: /magento-code-bulk-add-new-product-attribute-store-attribute-sets
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
  - Database
  - GIST
  - Import
  - Magento Code
  - PHP
---
This little script is an excellent time saver for adding a new attribute to all of the attribute sets configured in your Magento store.

There are a few attributes to update:

  * Replace `**ATTRIBUTE CODE**` with the code of the attribute you wish to add.
  * Replace `**ATTRIBUTE GROUP NAME**` with the group name
  * Replace `**SORT ORDER**` with sort order you want it to display, as you&#8217;d expect.

Upload the script to the Magento root folder and hit with your browser.

<script src="https://gist.github.com/keithgreer/bb9c6db921f3f14c68546bce6142073a.js"></script>
