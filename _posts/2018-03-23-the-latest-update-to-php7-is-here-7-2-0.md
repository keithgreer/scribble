---
id: 1163
title: 'The latest update to PHP7 is here&#8230; 7.2.0'
date: 2018-03-23T11:43:59+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1163
permalink: /the-latest-update-to-php7-is-here-7-2-0
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
image: /cms/wp-content/uploads/2017/06/php.png
categories:
  - Notes
tags:
  - PHP
---
This month PHP released the latest update PHP7.2.0. While PHP 7.2 is an improvement, it is not groundbreaking as the jump from PHP5.6 to PHP7.0. However the biggest change, having encryption as part of the standard library in PHP, is very exciting. As PHP7 evolves and developers get more interesting tools to work with there are more and more reasons for dumping PHP5 and embracing the change.

Amongst the security updates there are a few cool new features and a couple of significant deprecations. [Carlo Daniele has compiled a list here](https://kinsta.com/blog/php-7-2/).

## Running web applications on PHP7.2.0

### Magento2 & PHP7.2.0

If you&#8217;re running Magento2 now might not be the best time to upgrade your PHP installation. It is important to note that both `each()` and `mcrypt()` have been removed from PHP 7.2. So stick with PHP 7.1, it doesn&#8217;t reach its end of life until 2019. [Full list M2 requirements from Magento](http://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html).

### Magento 1 & PHP7

Out-of-the-box Magento 1.X installs are not designed to run on PHP7 at all. If you really need to run Magento 1.X on PHP7 Inchoo have created an our open-source compatibility extension for Magento and PHP 7 with impressive speed improvements. [Details here](https://inchoo.net/magento/its-alive/)&#8230;

### WordPress & PHP7.2

As you&#8217;d expect as long as your WordPress install is up to date it&#8217;ll run fine.