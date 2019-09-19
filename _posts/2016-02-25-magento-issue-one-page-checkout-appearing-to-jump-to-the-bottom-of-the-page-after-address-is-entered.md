---
id: 436
title: 'Magento Issue: One Page Checkout appearing to jump to the bottom of the page after address is entered'
date: 2016-02-25T11:25:05+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=436
permalink: /magento-issue-one-page-checkout-appearing-to-jump-to-the-bottom-of-the-page-after-address-is-entered
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
image: /cms/wp-content/uploads/2016/02/magento-generic.png
categories:
  - Code
tags:
  - Bugfixes
  - Magento
  - Magento Code
  - Magento Issues
---
This is a recurring issue with Magento&#8217;s standard One Page Checkout. It most often occurs when the template has been updated to include lots of big fonts and padding around field elements (thanks designers).

What happens is that the address stage is a very tall container which then jumps to the much shorter Shipping Method stage and the height of the entire page is updated in the browser, while you user thinks they&#8217;re being pushed to the bottom of the page.

The easy fix is to tell prototype.js to jump to the top of the next stage rather than remaining at the fixed position on the page.

In your checkout/onepage.phtml add the following code directly after the `var checkout = new Checkout()` block.

<pre>checkout.gotoSection = function (section, reloadProgressBlock) {
            Checkout.prototype.gotoSection.call(
               this, 
               section, 
               reloadProgressBlock
            );
            $('opc-' + section).scrollTo();
        };</pre>