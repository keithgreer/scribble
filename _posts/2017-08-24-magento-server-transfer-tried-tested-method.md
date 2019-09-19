---
id: 1025
title: 'Magento Server Transfer &#8211; Tried and Tested Method'
date: 2017-08-24T08:26:45+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1025
permalink: /magento-server-transfer-tried-tested-method
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
  - Notes
tags:
  - Bash
  - Command Line
  - FTP
  - Import
  - Magento
  - MySQL
---
Moving an entire Magento site from one server to another or between hosts can be a daunting task for non-server administrators.

I&#8217;m going to try and expand this over time.

  * Agree time frames, a day for file system sync, an hour for database update and DNS update.
  * **Content Freeze** &#8211; no new images or content is added by Store owner, customers continue to place orders and create accounts. 
      * A copy of the site is downloaded to the new server via FTP
      * A snapshot of the database is taken and used to test the site on the new server
  * **Database Freeze** &#8211; no new orders, holding page on the front end, Admin Panel still accessible if required but no updates allowed. 
      * Export/import database 
          * Old Server: mysqldump -u YourUser -p YourDatabaseName > wantedsqlfile.sql
          * New Server wget http://www.yourwebsite.com/wantedsqlfile.sql
          * New Server: mysql -u YourUser -p YourDatabaseName < wanted.sql
      * Copy over/configure your SSL for the new site
      * Next-up is the DNS update to repoint the domain
  * **Done**

&nbsp;