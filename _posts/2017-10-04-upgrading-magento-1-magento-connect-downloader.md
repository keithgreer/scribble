---
id: 1080
title: Upgrading Magento 1 through the Magento Connect Downloader
date: 2017-10-04T11:09:31+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1080
permalink: /upgrading-magento-1-magento-connect-downloader
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
  - Userguide
tags:
  - Configuration
  - Magento
  - Security
---
If you don&#8217;t fancy [upgrading Magento 1 through command line](https://keithgreer.uk/upgrading-magento-1-command-line), you can upgrade Magneto core using Magento&#8217;s in-built Magento Connect Downloader.

  * Load yoursite.com/downloader.
  * Login with a user who has full Magento permissions.
  * Make sure to click the &#8220;Clear all sessions after successful install or upgrade&#8221; option before proceeding.
  * Click the **Check for Upgardes** button
  * This will load all the packages with upgrade options beside them.
  * Find the package name `Mage_All_Latest`
  * In the dropdown choose the most recent version of `Mage_All_Latest`
  * Use the checkbox beside it to include it in the upgrade
  * Click **Commit Changes**

If you login and don&#8217;t see any packages, this may be due to the way the site was built.

At the top of Magento connect downloader enter `magento-core/Mage_All_Latest`  in the in put box, this will install all latest MagentoConnect core packages on top of existing files and will allow future upgrades through Magento Connect Downloader.