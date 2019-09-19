---
id: 188
title: Add Static Blocks to CMS Pages in Admin
date: 2015-05-10T09:26:27+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=188
permalink: /add-static-blocks-to-cms-pages-in-admin
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
  - Userguide
tags:
  - Magento
  - Magento Code
  - Static Blocks
  - WYSIWYG
---
Static Blocks are an easy way to include snippets of code or text on many pages throughout your Magento store. They can be used to make a promotion or your contact details and replicated throughout your site multiple times but to only require one update to change all of them.

<!--more-->

## Create your Block

First step is to create your static block in Magento Admin. Navigate to CMS > Static Blocks and click on the Add New Block. Give your block a descriptive title so you can tell what it’s used for. The identifier will be used as a code later, keep it lowercase and no spaces. Choose which store you want to use it on (more on that story later). Make sure it’s enabled and then you can enter the product promotion, banner or contact details in the content box.

## Add your block to CMS Pages

The next step is to add your block to CMS Pages, to do this you’ll need to navigate to Magento Admin and CMS > Manage pages. Choose the page you want to add the static block to and use the code below to add it to your CMS page…

<pre>{% raw %}{{block type=”cms/block” block_id=”identifier-code“}}{% endraw %}</pre>

Change identifier-code to the code your entered on your CMS Page.

Save that page and that’s that.
