---
id: 695
title: All-in-one Google Analytics tracking in Magento
date: 2016-11-08T12:41:31+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=695
permalink: /one-google-analytics-tracking-magneto
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
  - Analytics
  - Google Analytics
  - Magento Code
  - Tracking
---
Simple single script to add Google&#8217;s conversion tracking to your Magento ecommerce website. The code should be added into the footer.phtml file within your current template. The code includes tracking of catalogue browsing, checkout and new orders.

Simply replace all the `$googleConversionId` with your actual Google Conversion ID.

<pre>&lt;!-- Google Conversion Tracking --&gt;
&lt;?php $googleConversionId = ""; // Your conversion ID goes here ?&gt;
&lt;?php $page_type = Mage::app()-&gt;getFrontController()-&gt;getRequest()-&gt;getControllerName();
if($page_type == 'index') { ?&gt;
 &lt;script type="text/javascript"&gt;
 var google_tag_params = {
 ecomm_pagetype: 'home',
 ecomm_prodid: '',
 ecomm_totalvalue: 0
 };
 &lt;/script&gt;
&lt;?php } elseif($page_type == 'category') { ?&gt;
 &lt;script type="text/javascript"&gt;
 var google_tag_params = {
 ecomm_pagetype: 'category',
 ecomm_prodid: '',
 ecomm_totalvalue: 0
 };
 &lt;/script&gt;
&lt;?php } elseif($page_type == 'product') {
 $product_id = Mage::registry('current_product')-&gt;getId();
 $product_id = Mage::getModel('catalog/product')-&gt;load($product_id)-&gt;getSku();
 $product_price = Mage::registry('current_product')-&gt;getPrice();
 ?&gt;
 &lt;script type="text/javascript"&gt;
 var google_tag_params = {
 ecomm_pagetype: 'product',
 ecomm_prodid: '&lt;?php echo $product_id; ?&gt;',
 ecomm_totalvalue: parseFloat('&lt;?php echo $product_price; ?&gt;')
 };
 &lt;/script&gt;
&lt;?php } elseif($page_type == 'cart') { ?&gt;
 &lt;script&gt;
 var id = new Array();
 var price = new Array();
 &lt;/script&gt;
 &lt;?php
 $cart = Mage::getModel('checkout/session')-&gt;getQuote();
 foreach ($cart-&gt;getAllItems() as $item) {
 $product_id = $item-&gt;getProductId();
 $product_id = $item-&gt;getSku();
 $product_id_all = $product_id_all.','.$product_id ;
 $productPrice = $item-&gt;getProduct()-&gt;getPrice();
 $productPrice_all = $productPrice_all.','.$productPrice;
 ?&gt;
 &lt;Script&gt;
 id.push('&lt;?php echo $product_id; ?&gt;');
 price.push(parseFloat('&lt;?php echo $productPrice; ?&gt;'));
 &lt;/Script&gt;
 &lt;?php
 }
 $product_id_all=substr($product_id_all, 1);
 $productPrice_all=substr($productPrice_all, 1);
 ?&gt;
 &lt;script type="text/javascript"&gt;
 var google_tag_params = {
 ecomm_pagetype: 'cart',
 ecomm_prodid: id,
 ecomm_totalvalue: price
 };
 &lt;/script&gt;
 &lt;?php } elseif($page_type == 'onepage') { ?&gt;
 &lt;script&gt;
 var id = new Array();
 var price = new Array();
 &lt;/script&gt;
 &lt;?php
 $cart = Mage::getModel('checkout/session')-&gt;getQuote();
 foreach ($cart-&gt;getAllItems() as $item)
 {
 $product_id = $item-&gt;getProductId();
 $product_id = $item-&gt;getSku();
 $product_id_all = $product_id_all.','.$product_id ;
 $productPrice = $item-&gt;getProduct()-&gt;getPrice();
 $productPrice_all = $productPrice_all.','.$productPrice;
 ?&gt;
 &lt;Script&gt;
 id.push('&lt;?php echo $product_id; ?&gt;');
 price.push(parseFloat('&lt;?php echo $productPrice; ?&gt;'));
 &lt;/Script&gt;
 &lt;?php } 
 $product_id_all=substr($product_id_all, 1);
 $productPrice_all=substr($productPrice_all, 1);
 ?&gt;
 &lt;script type="text/javascript"&gt;
 var google_tag_params = {
 ecomm_pagetype: 'purchase',
 ecomm_prodid: id,
 ecomm_totalvalue: price
 };
 &lt;/script&gt;
 &lt;?php }else{ ?&gt;
 &lt;script type="text/javascript"&gt;
 var google_tag_params = {
 ecomm_pagetype: 'other',
 ecomm_prodid: '',
 ecomm_totalvalue: 0
 };
 &lt;/script&gt;
 &lt;?php } ?&gt;
&lt;script type="text/javascript"&gt;
 /* &lt;![CDATA[ */
 var google_conversion_id = &lt;?php echo $googleConversionId; ?&gt;;
 var google_custom_params = window.google_tag_params;
 var google_remarketing_only = true;
 /* ]]&gt; */
&lt;/script&gt;
&lt;script type="text/javascript" src="//www.googleadservices.com/pagead/conversion.js"&gt;
&lt;/script&gt;
&lt;noscript&gt;
 &lt;div style="display:inline;"&gt;
 &lt;img height="1" width="1" style="border-style:none;" alt="" src="//googleads.g.doubleclick.net/pagead/viewthroughconversion/&lt;?php echo $googleConversionId; ?&gt;/?value=0&amp;guid=ON&amp;script=0"/&gt;
 &lt;/div&gt;
&lt;/noscript&gt;
&lt;!-- End Google Conversion Tracking --&gt;</pre>