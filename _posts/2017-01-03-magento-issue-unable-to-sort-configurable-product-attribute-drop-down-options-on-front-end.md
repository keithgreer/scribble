---
id: 549
title: 'Magento Issue: Unable to sort configurable product attribute drop down options'
date: 2017-01-03T09:00:44+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=549
permalink: /magento-issue-unable-to-sort-configurable-product-attribute-drop-down-options-on-front-end
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
  - Magento Issues
  - PHP
---
Having encountered this issue a couple of times I though it was time to make a note. This is a fix for an issue in Magento 1.9 whereby the order specified for option attributes in the admin panel are not being applied on the front end.

Jonathon Byrd at Merchant Protocol has published [this fix](https://merchantprotocol.com/knowledgebase/solved-sort-configurable-product-attribute-options-and-dropdowns/) which overrides the core Configurable Attribute Collection class with an updated one which properly sorts the attribute options by the sort value in the Admin panel.

» [[Solved] Sort Configurable Product Attribute Options and Dropdowns](https://merchantprotocol.com/knowledgebase/solved-sort-configurable-product-attribute-options-and-dropdowns/)

Jonathon&#8217;s fix works perfectly. I&#8217;ve implemented it alongside a simple product pricing module for configurable products also without issue.