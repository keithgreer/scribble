---
id: 889
title: Magento header.phtml basic user account and basket code
date: 2017-03-22T13:40:16+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=889
permalink: /magento-header-phtml-basic-user-account-basket-code
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
  - Magento Code
  - PHP
---
Some useful shippets for including customer accound and a basic basket/cart product count in the header of Magento. This should be added to header.html in your template folder, athough the code will work anywhere in the Magento template system

<!--more-->

## Login and log out links

<pre>&lt;ul&gt;
   &lt;?php if ($this-&gt;helper('customer')-&gt;isLoggedIn() ) { ?&gt;
      &lt;li&gt;&lt;a href="/customer/account/logout/"&gt;Log out&lt;/a&gt;&lt;/li&gt;
      &lt;!-- &lt;li&gt;&lt;a href="/customer/account/create/"&gt;Register&lt;/a&gt;&lt;/li&gt; --&gt;
   &lt;?php } else { ?&gt;
      &lt;li&gt;&lt;a href="/customer/account/login/"&gt;Sign in&lt;/a&gt;&lt;/li&gt;
      &lt;li&gt;&lt;a href="/customer/account/create/"&gt;Register&lt;/a&gt;&lt;/li&gt;
   &lt;?php } // logged in ?&gt;
&lt;/ul&gt;</pre>

## **Simple code to dispay cart count**

<pre>&lt;ul&gt;
&lt;?php
   $count = $this-&gt;helper('checkout/cart')-&gt;getSummaryCount();  //get total items in cart
   $total = $this-&gt;helper('checkout/cart')-&gt;getQuote()-&gt;getGrandTotal(); //get total price
   if($count&gt;1) {
      echo $this-&gt;__('&lt;li&gt;&lt;a href="/checkout/cart"&gt;&lt;strong&gt;Basket (%s Items)&lt;/strong&gt;&lt;/a&gt;&lt;/li&gt;',$count);
   } else if ($count==1) {
      echo $this-&gt;__('&lt;li&gt;&lt;a href="/checkout/cart"&gt;&lt;strong&gt;Basket (1 Item)&lt;/a&gt;&lt;/li&gt;&lt;/strong&gt;',$count);
   } else {
      echo $this-&gt;__('&lt;li&gt;&lt;a href="/checkout/cart"&gt;&lt;strong&gt;Basket (0 Items)&lt;/strong&gt;&lt;/a&gt;&lt;/li&gt;',$count);
   }
   ?&gt; 
&lt;/ul&gt;</pre>