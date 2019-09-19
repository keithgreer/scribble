---
id: 1147
title: CMS blocks disappear after version 1.9.2.2 upgrade or SUPEE-6788 patch
date: 2018-02-08T17:09:57+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1147
permalink: /cms-blocks-disappear-version-1-9-2-2-upgrade-supee-6788-patch
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
  - .phtml Templates
  - Magento Issues
  - Static Blocks
---
Magento veresion 1.9.2.2 and patch SUPEE-6788 both introduce a new security featuer to Magento. Blocks on the front-end have to be enabled or whitelisted before it will work.

Blocks can be added via a new Admin Panel section under Permissions > Blocks. Adding or allowing a new block is pretty streight forward:

  1. Navigate to `System > Permissions > Blocks`
  2. Click &#8220;Add New Block&#8221;
  3. Enter the block name: e.g. `cms/block`*
  4. Set &#8220;Is Allowed&#8221; to Yes

* Replace this with the name of the block that has disappeared