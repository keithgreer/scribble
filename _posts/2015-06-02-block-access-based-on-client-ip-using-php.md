---
id: 190
title: Block access based on Client IP using PHP
date: 2015-06-02T09:35:24+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=190
permalink: /block-access-based-on-client-ip-using-php
categories:
  - Code
  - Notes
tags:
  - IP
  - PHP
---
This is a useful script to add at the start of any PHP file which you want hidden from a specific IP address or addresses. Antyhing below this first script will be hidden from anyone listed in the $valid_ips array.
  
<!--more-->

<pre>$valid_ips = array('123.123.123.123','32.23.13.31','123.45.678.90');
if (in_array($_SERVER['REMOTE_ADDR'],$valid_ips)) {
   echo "You do not have permission to access this website";
   exit();
}</pre>

## PHP: Grant access based on Client IP

The opposite requires a simple exclamation mark before in_array() to change the script so that only those listed in the array will be allowed to see the site. Anything below this code will only be accessible IPs is in the array. 

<pre>$valid_ips = array('123.123.123.123','32.23.13.31','123.45.678.90');
if (!in_array($_SERVER['REMOTE_ADDR'],$valid_ips)) {
   echo "You do not have permission to access this website";
   exit();
}</pre>