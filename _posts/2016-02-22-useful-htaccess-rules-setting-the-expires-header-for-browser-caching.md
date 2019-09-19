---
id: 421
title: 'Useful .htaccess Rules: Setting the expires header for browser caching'
date: 2016-02-22T12:19:31+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=421
permalink: /useful-htaccess-rules-setting-the-expires-header-for-browser-caching
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
  - .htaccess
  - Caching
  - Website Optimisation
---
Expires headers let the browser know whether to server a cached version of the page. This can simultaneously help to reduce server load and increase page load time by telling the browser that it doesn&#8217;t have to check for new versions of files for an extended period.

The code below will allow images to be cached for a year and text-based content to be cached for one month. For most fairly static websites (like this one) that doesn&#8217;t change very often aside for a new post now and then this should be more then enough.

If you are running a dynamic website be careful with any sensitive information which may be stored, for example  JSON responses, user account pages and the like should be set-up to not cache.

<pre>## START keithgreer.uk EXPIRES CACHING ##
ExpiresActive On
ExpiresByType image/jpg "access 1 year"
ExpiresByType image/jpeg "access 1 year"
ExpiresByType image/gif "access 1 year"
ExpiresByType image/png "access 1 year"
ExpiresByType text/css "access plus 1 month"
ExpiresByType text/html "access 1 month"
ExpiresByType application/pdf "access 1 month"
ExpiresByType text/x-javascript "access 1 month"
ExpiresByType image/x-icon "access 1 year"
ExpiresDefault "access 1 month"
## END keithgreer.uk EXPIRES CACHING ##
</pre>

The above can be copied into your .htaccess file without any major issues but, of course best checked before deploying to a live environment.

&nbsp;