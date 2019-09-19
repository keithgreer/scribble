---
id: 715
title: Session Management and Validation Settings in Magento Configuration
date: 2016-11-18T11:45:32+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=715
permalink: /session-management-validation-settings-magento-configuration
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
image: /cms/wp-content/uploads/2016/03/padlock.png
categories:
  - Notes
tags:
  - Configuration
  - Magento
  - Website Optimisation
---
Cookie and session management is an important aspect of any ecommerce store. Everything from a customer&#8217;s cart, checkout process and recently viewed products is made possible by knowing who is using the website. This is where cookies come into play.

The _Session Cookie Management_ options specify how and where cookies are set and used in your Magento store.

The _Session Validation Settings_ ensure the safety of the information stored in sessions by checking known information gathered from previous visits by a customer matches the current information.

## Session Cookie Management

<pre><img class="alignnone size-full wp-image-716 aligncenter" src="https://keithgreer.uk/cms/wp-content/uploads/2016/11/session-cookie-management.png" alt="session-cookie-management" width="676" height="192" srcset="https://keithgreer.uk/cms/wp-content/uploads/2016/11/session-cookie-management.png 676w, https://keithgreer.uk/cms/wp-content/uploads/2016/11/session-cookie-management-300x85.png 300w" sizes="(max-width: 676px) 100vw, 676px" /></pre>

  * **Cookie Lifetime** is the time a cookie will remain &#8216;alive&#8217; if the customer returns to the website within this timescale (in seconds) their cart/checkout/details will have been stored. If the cookie expires that information is no longer available to the customer
  * **Cookie Path** will usually just need a forward slash &#8220;/&#8221;, that means the cookie will be available across the domain and nto be limited to a specific directory.
  * The **Cookie Domain** will usually be your domain name preceded by a dot, and excluding the &#8220;www&#8221;. This means the cookie will be available on all sub domains
  * **Use HTTP Only** should usually be set to &#8216;yes&#8217;, this means that the cookie will remain active as the user switches between http:// and https://. If this is set to &#8216;no&#8217; you will experience the customer&#8217;s cart emptying as they switch between non-SSL and SSL versions of the site, which is usually when clicking through through to the checkout.
  * **Cookie Restriction Mode** will notify your visitors that cookies are required for full-featured operations. It relates specifically to <a href="https://www.cookielaw.org/the-cookie-law/" target="_blank">EU cookie directive</a>.

## Session Validation Settings

<pre><img class="aligncenter size-full wp-image-717" src="https://keithgreer.uk/cms/wp-content/uploads/2016/11/session-validation-settings.png" alt="session-validation-settings" width="676" height="243" srcset="https://keithgreer.uk/cms/wp-content/uploads/2016/11/session-validation-settings.png 676w, https://keithgreer.uk/cms/wp-content/uploads/2016/11/session-validation-settings-300x108.png 300w" sizes="(max-width: 676px) 100vw, 676px" /></pre>

  * **Validate REMOTE_ADDR** checks that the customer&#8217;s public IP address is the same
  * **Validate HTTP_VIA** verifies that the proxy address of an incoming request matches what is stored
  * **Validate HTTP\_X\_FORWARDED_FOR** checks that the forwarded-for address of a request matches what was stored previously.
  * **Validate HTTP\_USER\_AGENT** checks that the browser/device matches previous visits.
  * **Use SID on Frontend** adds a ID to the end of URLs that allows Magento to recognise visitors as they pass between domains set-up on the one Magento install.