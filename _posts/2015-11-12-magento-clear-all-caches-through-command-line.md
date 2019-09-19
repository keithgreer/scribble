---
id: 423
title: 'Magento: Clear all caches through command line'
date: 2015-11-12T20:21:21+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=423
permalink: /magento-clear-all-caches-through-command-line
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
  - Code
tags:
  - Bash
  - Command Line
  - Linux
  - Magento
  - Magento Code
---
When making certain changes to Magento, such as modifying source files, installing extensions, reverting changes, it is necessary to clear the cache in order for the changes to become visible. 

Oftentimes the Admin Panel > System -> Cache Management then &#8220;Flush Magento Cache&#8221; will not have the desired affect.

## Command Line

Delete the contents of the **var/cache/** folder using the following Linux SSH command. This command MUST be executed from your Magento base directory for it to work properly.

<pre>rm -rf var/cache/*</pre>

After the cache has been wiped, session values will also need to be cleared from the system. This command MUST be executed from your Magento base directory for it to work properly.

<pre>rm -rf var/session/*</pre>

Finally once the site has been cleared of old cached and logged data for best results a complete Reindex of the site is recommended. 

<pre>php shell/indexer.php --reindexall</pre>

## [ka.lpe.sh Script](http://ka.lpe.sh/2014/06/22/magento-clear-all-caches-from-command-line/)

ka.lpe.sh have put together a really good script for programmatically clearing the cash from SSH. Create a file in your Magento root and name it clearCache.php with the below code:

  * <http://ka.lpe.sh/2014/06/22/magento-clear-all-caches-from-command-line/>