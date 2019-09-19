---
id: 962
title: Create a custom URL rewrite/redirect in Magento
date: 2017-05-24T10:05:54+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=962
permalink: /create-custom-url-rewriteredirect-magento
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
  - Userguide
tags:
  - Configuration
  - Magento
  - Website Optimisation
---
You can use a custom rewrite to redirect CMS pages, or any other type of page. For example, if you change the URL key of the privacy policy from privacy-policy-cookie-restriction-mode to privacy-policy, the link in the cookie restriction mode will return “404 &#8211; Page Not Found.” To redirect traffic to the new URL key, create a custom rewrite with the following settings:

ID Path: `privacy-policy`
  
Request Path: `privacy-policy-cookie-restriction-mode`
  
Target Path: `privacy-policy`
  
Redirect: `Permanent (301)`

Before you begin, figure out the URL keys that you need for the ID Path, Request Path, and Target Path. Just remember— the “Request Path” is the old URL, and the “ID Path” and “Target Path” are the new URL.