---
id: 374
title: PayPal IPN notification errors with Magento
date: 2016-02-02T11:37:32+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=374
permalink: /paypal-ipn-notification-errors-with-magento
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
image: /cms/wp-content/uploads/2016/02/paypal.png
categories:
  - Notes
tags:
  - Magento
  - Payment Gateways
  - PayPal
---
This one has popped up a few times in the past. When PayPal has been set-up and configured to with Magento the store owner receives the email below seemingly randomly.

## Log into your PayPal Account

  * Click into &#8216;Profile&#8217;
  * Scroll down to the bottom of the page and under &#8216;Selling Preferences&#8217; on the right-hand side
  * Click on &#8216;Instant Payment Notification Preferences&#8217;
  * Click &#8216;Edit IPN Settings&#8217;

You can check that &#8220;Do not receive IPN messages&#8221; is set to enabled.

## What&#8217;s the issue?

The error appears when the Magento store has been set-up correctly but the store owner also uses PayPal as a payment method on another service. For example eBay, another store etc.

When a payment is made through one of these services PayPal will still try and send a PayPal IPN notification to your store, for an order it didn&#8217;t originally process. The notification fails and PayPal think&#8217;s something dodgy is up.

> Dear xxxx,
> 
> Please check your server that handles PayPal Instant Payment Notifications (IPN). Instant Payment Notifications sent to the following URL(s) are failing:
> 
> http://magentostore.example/paypal/ipn/
> 
> If you do not recognize this URL, you may be using a service provider that is using IPN on your behalf. Please contact your service provider with the above information. If this problem continues, IPNs may be disabled for your account.
> 
> Thank you for your prompt attention to this issue.
> 
> Yours sincerely, PayPal

&nbsp;