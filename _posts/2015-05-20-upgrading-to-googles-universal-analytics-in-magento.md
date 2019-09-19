---
id: 195
title: 'Upgrading to Google&#8217;s Universal Analytics in Magento'
date: 2015-05-20T09:37:20+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=195
permalink: /upgrading-to-googles-universal-analytics-in-magento
categories:
  - Code
  - Notes
tags:
  - Analytics
  - eCommerce
  - Google Analytics
  - Magento Code
---
The new Google Universal Analytics provides the opportunity for own measurement values and dimensions and allow you to track usage across platforms. Universal Analytics introduces a set of features that change the way data is collected and organized in your Google Analytics account, so you can get a better understanding of how visitors interact with your online content.

## Updating Code

Unless you&#8217;re using advanced features the upgrade process for most people will be pretty easy. Find where your code is installed on your website and replace&#8230;

<pre>&lt;script type="text/javascript"&gt;

  var _gaq = _gaq || [];
  _gaq.push(['_setAccount', 'UA-XXXXX-X']);
  _gaq.push(['_trackPageview']);

  (function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
  })();

&lt;/script&gt;</pre>

&#8230;With the Universal Analytics code (adding your Analytics ID to the code)&#8230;

<pre>&lt;!-- Google Analytics --&gt;
&lt;script&gt;
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','//www.google-analytics.com/analytics.js','ga');

ga('create', 'UA-XXXX-Y', 'auto');
ga('send', 'pageview');

&lt;/script&gt;
&lt;!-- End Google Analytics --&gt;</pre>

Save it and upload, then login to Google Analytics and upgrade your account there to start recieving your analytics.

## Upgrade to Universal Analytics

If you&#8217;re using more advanced analytics Google has put together a pretty useful [guide to upgrading your code from ga.js to analytics.js](https://developers.google.com/analytics/devguides/collection/upgrade/guide). The Universal Analytics Upgrade is a two step process you can follow to turn all of your classic Analytics properties into Universal Analytics properties and implement a Universal Analytics tracking code.