---
id: 1204
title: 'Magento2 CLI: Set Ubuntu PHP Version to match LAMPP/XAMPP'
date: 2018-06-04T11:35:10+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1204
permalink: /magento2-cli-set-ubuntu-php-version-to-match-lampp-xampp
meta_description:
  - ""
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
---
The Magento2 Comand Line Interface (CLI) needs to use the same version of PHP as your local web environment. You can check this by setting up an info.php script with in it &#8220;`<?php phpinfo();`&#8221; and comparing the output with the command &#8220;`$ which php`&#8220;.

You may find you are running two different versions of PHP each with its own PHP executable: by default one will be located in /usr/bin and another in somewhere like /opt/lampp/bin.

If you want to execute /opt/lampp/bin/php instead of /usr/bin, open your .bashrc file

<pre>sudo nano ~/.bashrc</pre>

At the very end add a new line:

<pre>PATH=/opt/lampp/bin:$PATH</pre>

Once you have saved .bashrc, run the command:

<pre>source .bashrc</pre>

You will now find bash is running the same PHP version and environment as your web server