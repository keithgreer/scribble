---
id: 687
title: All-in-one Facebook Pixel Code for Magento ecommerce
date: 2016-11-08T12:20:30+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=687
permalink: /one-facebook-pixel-code-magento-ecommerce
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
image: /cms/wp-content/uploads/2016/09/pixel.png
categories:
  - Code
tags:
  - Facebook Pixel Code
  - Magento Code
  - Reporting
  - Tracking
---
Simple single script to add Facebook&#8217;s Pixel Code tracking to your Magento ecommerce website. The code should be added into the head.phtml file within your template. This includes tracking of search and checkout progress and new orders.

Simply replace all the `$facebookPixelId` with your actual Facebook Pixel Code ID.

<pre>&lt;!-- All in one Facebook Pixel Code --&gt; 
&lt;?php $facebookPixelId = "000000000000000000000"; // Your Pixel Code goes here ?&gt;
&lt;script&gt; 
 !function(f,b,e,v,n,t,s){if(f.fbq)return;n=f.fbq=function(){n.callMethod? 
 n.callMethod.apply(n,arguments):n.queue.push(arguments)};if(!f._fbq)f._fbq=n; 
 n.push=n;n.loaded=!0;n.version='2.0';n.queue=[];t=b.createElement(e);t.async=!0; 
 t.src=v;s=b.getElementsByTagName(e)[0];s.parentNode.insertBefore(t,s)}(window, 
 document,'script','//connect.facebook.net/en_US/fbevents.js');
 fbq('init', '&lt;?php echo $facebookPixelId; ?&gt;'); 
 fbq('track', "PageView");
&lt;?php 
 $request = $this-&gt;getRequest();
 $module = $request-&gt;getModuleName();
 $controller = $request-&gt;getControllerName();
 $action = $request-&gt;getActionName();
 $pageIdentifier = Mage::app()-&gt;getFrontController()-&gt;getAction()-&gt;getFullActionName(); 
 // Lead
 if(Mage::registry('current_product')) {
 echo "fbq('track', 'Lead');";
 }
 // Search
 if($controller == 'result' || $controller =='advanced') { 
 echo "fbq('track', 'Search');"; 
 }
 // Customer registration
 if($module == 'customer' && $controller == 'account' && $action == 'index'){
 echo "fbq('track', 'CompleteRegistration')";
 }
 // Add to cart
 if($module == 'checkout' && $controller == 'cart' && $action == 'index') {
 echo "fbq('track', 'AddToCart');";
 }
 // Add to wishlist
 if($module == 'wishlist') {
 echo "fbq('track', 'AddToWishlist');";
 }
 // Checkout start 
 if(Mage::getURL('checkout/onepage') == Mage::helper('core/url')-&gt;getCurrentUrl()) {
 echo "fbq('track', 'InitiateCheckout');";
 
 // As the onepagecheckout don't have a specific page for add billing info, i placed the tracker here
 echo "fbq('track', 'AddPaymentInfo');";
 }
 // Checkout success
 if ($pageIdentifier == 'transparente_standard_redirect') {
 $lastOrderId = Mage::getSingleton('checkout/session')-&gt;getLastOrderId();//Geeting last order id
 $order = Mage::getSingleton('sales/order'); //getting order model
 $order-&gt;load($lastOrderId); //loding current order
 $_totalData =$order-&gt;getData(); //loading order model data
 $grandTotal = number_format($_totalData['grand_total'],2,'.',''); //loading grand total
 echo "fbq('track', 'Purchase', {value: '$grandTotal', currency: 'BRL'});";
 }
 ?&gt;
&lt;/script&gt; 
&lt;noscript&gt;&lt;img height="1" width="1" style="display:none" 
src=" https://www.facebook.com/tr?id=&lt;?php echo $facebookPixelId; ?&gt;&ev=PageView&noscript=1" 
/&gt;&lt;/noscript&gt; 
&lt;!-- All in one End Facebook Pixel Code --&gt;</pre>