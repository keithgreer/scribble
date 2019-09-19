---
id: 280
title: PHP Storm and making FTP connections with SSL (FTPS)
date: 2015-11-24T10:59:13+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=280
permalink: /php-storm-and-making-ftp-connections-with-ssl-ftps
categories:
  - Notes
tags:
  - Deployment
  - FTP
  - PHP Storm
---
If you&#8217;re having issues connecting to a server via FTPS in phpStorm I found that the magic combination for PHP Storm and FTP-SSL connections is&#8230;

  * Type: **FTPS**
  * SSL: **Explicit**
  * Passive Mode: **On**
  * Protected data channel: **<default>**

In particular the Protected data channel was set to &#8220;PRTO C&#8221; by default on my install and it was that causing the bother.

**Error Message**:

<pre>[23/11/2015 12:13] Failed to transfer file 'C:\web\htdocs\
•••••\••••••••••••\test.txt': cant open output connection for
file "ftps://•••.•••.•••.•••/test.txt". Reason: "500 I won't 
open a connection to 192.•••.•••.••• (only to 81.•••.•••.•••)".</pre>

**Solution**

[<img class="alignnone size-full wp-image-281" src="https://keithgreer.uk/cms/wp-content/uploads/2015/11/php-storm-ftps-ftp-ssl-settings.png" alt="php-storm-ftps-ftp-ssl-settings" width="979" height="823" srcset="https://keithgreer.uk/cms/wp-content/uploads/2015/11/php-storm-ftps-ftp-ssl-settings.png 979w, https://keithgreer.uk/cms/wp-content/uploads/2015/11/php-storm-ftps-ftp-ssl-settings-300x252.png 300w" sizes="(max-width: 979px) 100vw, 979px" />](https://keithgreer.uk/cms/wp-content/uploads/2015/11/php-storm-ftps-ftp-ssl-settings.png)

See also: [JetBrains PHP Storm: Creating a remote server configuration](https://www.jetbrains.com/phpstorm/help/creating-a-remote-server-configuration.html)