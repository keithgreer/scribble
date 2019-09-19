---
id: 1212
title: Start/Stop XAMPP on Ubuntu using Terminal
h1: Running XAMPP on Ubuntu using Terminal 
date: 2018-06-12T09:16:03+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1212
permalink: /running-xampp-on-ubuntu-using-terminal
---
To start XAMPP run the following and the command will return a list of running services: 

<pre>sudo /opt/lampp/lampp start</pre>

![Start XAMPP](https://keithgreer.uk/wp-content/uploads/2018/06/bash.lampp_.start_.png "Start XAMPP")

To stop XAMPP run the command below and it will return a list of the stopped services. 

<pre>sudo /opt/lampp/lampp stop</pre>

![Stop XAMPP](https://keithgreer.uk/wp-content/uploads/2018/06/bash.lampp_.stop_.png "Stop XAMPP")

You can also stop/start/restart individual services by appending &#8220;apache&#8221;, &#8220;mysql&#8221; or &#8220;ftp&#8221; to the end. 

![Ubuntu Help screen for XAMPP](https://keithgreer.uk/wp-content/uploads/2018/06/bash.lampp_.help_.png "Ubuntu Help screen for XAMPP")

### Starting

`start` &#8211; Start XAMPP (Apache, MySQL and eventually others)
	  
`startapache` &#8211; Start only Apache
	  
`startmysql` &#8211; Start only MySQL
	  
`startftp` &#8211; Start only ProFTPD

### Stopping

`stop` &#8211; Stop XAMPP (Apache, MySQL and eventually others)
	  
`stopapache` &#8211; Stop only Apache
	  
`stopmysql` &#8211; Stop only MySQL
	  
`stopftp` &#8211; Stop only ProFTPD

### Restart

`reload` &#8211; Reload XAMPP (Apache, MySQL and eventually others)
	  
`reloadapache` &#8211; Reload only Apache
	  
`reloadmysql` &#8211; Reload only MySQL
	  
`reloadftp` &#8211; Reload only ProFTPD
	  
`restart` &#8211; Stop and start XAMPP

### SSL & Security

`security` &#8211; Check XAMPP&#8217;s security
	  
`enablessl` &#8211; Enable SSL support for Apache
	  
`disablessl` &#8211; Disable SSL support for Apache

### Config

`backup` &#8211; Make backup file of your XAMPP config, log and data files
	  
`oci8` &#8211; Enable the oci8 extenssion

### GUI Panel

`panel` &#8211; Starts graphical XAMPP control panel
