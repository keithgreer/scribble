---
id: 198
title: Add Google Analytics ecommerce:addTransaction to your Magento Store
date: 2015-05-15T09:38:12+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=198
permalink: /add-google-analytics-ecommerceaddtransaction-to-your-magneto-store
categories:
  - Code
  - Notes
tags:
  - Analytics
  - Google Analytics
  - Magento Code
  - PHP
---
A quick and way way to record transactions to Google Universal Analytics.

First add this piece of PHP to your success page at the end of the checkout process. Update the template in magento/app/design/frontend/your/theme/template/checkout/success.phtml. This will retreve the order details&#8230;

<pre>&lt;?php
$order = Mage::getModel('sales/order')-&gt;loadByIncrementId($this-&gt;getOrderId());
$total = $order-&gt;getGrandTotal();
$shipping = $order-&gt;getShippingAmount();
$tax = $order-&gt;getTaxAmount();
$store = Mage::app()-&gt;getStore();
$name = $store-&gt;getName();
?&gt;</pre>

Then add the following JavaScript, it first loads the ecommerce.js plugin for Universal Analytics &#8211; you don&#8217;t need to include this if it has already been called elsewhere. ten the following lines add the details of the transaction and finally it sends the transaction details back to Google Analytics.

<pre>&lt;script type="text/javascript"&gt;

ga('require', 'ecommerce', 'ecommerce.js'); // Load GA ecommerce plug-in.
ga('ecommerce:addTransaction', {
'id': '&lt;?php echo $this-&gt;getOrderId(); ?&gt;', // Transaction ID. Required
'affiliation': '&lt;?php echo $name ?&gt;', // Affiliation or store name
'revenue': '&lt;?php echo $total; ?&gt;', // Grand Total
'shipping': '&lt;?php echo $shipping; ?&gt;', // Shipping
'tax': '&lt;?php echo $tax; ?&gt;' // Tax
});
ga('ecommerce:send');

&lt;/script&gt;</pre>

**Coming soon:** How to [record individual cart line items as well as the transaction](http://code.keithgreer.uk/2014/02/28/magento-code-google-analytics-ecommerceadditem-on-success-phtml) details so product popularity can be monitored.