---
id: 192
title: Useful .gitattributes defaults for Beanstalk Git
date: 2015-05-25T09:36:27+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=192
permalink: /useful-gitattributes-defaults-for-beanstalk-git
categories:
  - Code
  - Notes
tags:
  - Beanstalk
  - GIT
  - gitattributes
---
Some useful copy-and-paste lines for the .gitattributes file when using Beanstalk Git. 

## Image and other binary files

Upload and store images as binary files, rather than text &#8211; the default. This will stop images being corrupted upon commit/push.

<!--more-->

<pre>*.png binary
*.gif binary
*.jpg binary
*.jpeg binary</pre>

## Dealing with line endings

Handle line endings automatically for files detected as text and leave all files detected as binary untouched.

<pre>* text eol=lf</pre>

The above will handle all files NOT found below it. The lines below should be added as the files are text and should be normalized (Convert crlf => lf)

*.gitattributes text eol=lf
  
.gitignore text eol=lf