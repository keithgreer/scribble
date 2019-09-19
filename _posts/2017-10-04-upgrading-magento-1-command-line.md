---
id: 1076
title: Upgrading Magento 1 through command line
date: 2017-10-04T10:57:08+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1076
permalink: /upgrading-magento-1-command-line
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
  - Command Line
  - Linux
  - Magento
  - Security
---
<p style="padding-left: 30px;">
  <em>Alternative: <a href="https://keithgreer.uk/upgrading-magento-1-magento-connect-downloader">Upgrade Magneto using the Magento Connect Downloader</a></em>
</p>

Upgrading Magento is a must to keep your store in top-top condition, protect your customers and your business.

Upgrading Magento through command line is the easiest way to make sure you are running the latest version of the Magento Software

  * Load the root directory of your Magento store
  * Make sure the &#8220;mage&#8221; file has the right permissions: `chmod 777 mage`
  * Then launch Magento set-up: `./mage mage-setup`
  * If all goes well you can then pull the latest version of the code source code:
  
    `./mage install http://connect20.magentocommerce.com/community Mage_All_Latest --force`

If things didn&#8217;t go well with mage-setup you may need to run set som preferences&#8230;.

  1. Make sure your prefered code is set: `./mage config-set preferred_state stable`
  2. Then sync your changes: `./mage sync`

You can then try the install command again.

That should do the trick.

&nbsp;