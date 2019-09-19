---
id: 399
title: MySQL Database Backup and Restore via Command Line (Copy-and-pasteable)
date: 2016-02-05T16:39:22+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=399
permalink: /mysql-database-backup-and-restore-copy-and-pasteable
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
image: /cms/wp-content/uploads/2016/02/mysql.png
categories:
  - Code
tags:
  - Bash
  - Command Line
  - Database
  - Linux
  - MySQL
---
Putting this together because I always end up checking online for the correct bash commands for Linux. These commands rely on your knowing for sure which database is which and you should always double check to be sure. 

## Export

First step is to go to use `cd` to change directory to the one in which you want the SQL Dump to appear. The dump will consist of a text file and all the database structure and content included.

<pre>cd var/www/example.com</pre>

If you want to double check the contents of the directory you are in then simply enter `ls` and a list of directories and files will be returned. 

<pre>ls</pre>

When you&#8217;re happy you&#8217;re in the right directory, we can export the file. In this instance I have a user name (`user123`) after the `-u`and the database is `database_live` and the initial `-p` means bash will ask me for the password. 

<pre>mysqldump -p -uuser123 database_live > mydumpfile.sql</pre>

Hit enter, enter the password and after some serious thinking (depending on the size of the database) you&#8217;ll be able to enter the next command. Again, entering `ls` will allow you to verify there is a file called mydumpfile.sql in the directory. 

## Import

The next step is then to import the database into your other database. It should be noted that importing the previous dump will with default configuration wipe any existing data during the import into the second database.

In the instance below I have a user name (`uuser456` ) after the `-u`and the database is `database_live` and the initial `-p` means bash will ask me for the password. 

<pre>mysql -p -uuser456 database_backup &lt; mydumpfile.sql</pre>

Hit enter, enter the password for the user and again it will hang while the details are imported.