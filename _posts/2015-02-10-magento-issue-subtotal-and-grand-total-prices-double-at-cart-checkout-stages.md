---
id: 410
title: 'Magento Issue: Subtotal and Grand Total prices double at Cart/Checkout stages'
date: 2015-02-10T14:36:38+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=410
permalink: /magento-issue-subtotal-and-grand-total-prices-double-at-cart-checkout-stages
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
  - Magento Issues
  - PHP
---
Have recently encountered an issue with prices in Magento Checkout appearing doubled. There are a number of solutions online which seem to (in various combinations) do the trick. 

A particular cause of the error seems to be when more than two addresses appear in the sales\_flat\_quote_address table. 

## Disable Third Party Checkouts

This seems to be the best solution, the issue predominantly happening when a third party one page checkout extension is in use. 

## [Dave Boyce Solution](http://www.daveboyce.com/double-order-totals-in-magento/)

This code removes anything other than two addresses being pulled for a quote from the table sales\_flat\_quote_address. The quick fix goes in `Mage\Checkout\Model\Cart.php`.

In The Mage\_Checkout\_Model_Cart class init() function enter the code below the line: `$this->getQuote()->setCheckoutMethod('');`

<pre>$addresses = $this-&gt;getQuote()-&gt;getAllAddresses();
    
if (count($addresses) &gt; 2) {
  for($i = 2; $i &lt; count($addresses); $i++) {
    $address = $addresses[$i];
    $address-&gt;isDeleted(true);
  }
}</pre>

## Multiple Address Checkout

It should also be check that under System > Configuration > Shipping Settings that &#8220;Maximum Qty Allowed for Shipping to Multiple Addresses&#8221; is set the value to &#8220;0&#8221;. The default is 100. 

To fix, change &#8220;Allow shipping to multiple address&#8221; to &#8220;Yes&#8221; and Save. Then Set Allow Shipping to &#8220;No&#8221; and set Maximum Addresses to &#8220;0&#8221;. Click Save.