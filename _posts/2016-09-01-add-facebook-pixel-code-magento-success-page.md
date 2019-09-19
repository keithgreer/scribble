---
id: 632
title: Add Facebook Pixel Code to Magento Success Page
date: 2016-09-01T10:59:33+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=632
permalink: /add-facebook-pixel-code-magento-success-page
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
  - Analytics
  - Facebook Pixel Code
  - Magento Code
  - Tracking
---
<div style="background:#fce6e2; border:1px solid #ccc; margin-bottom:1em; padding:1em; ">
  <strong>Update:</strong> Instead of this, try the <a href="https://keithgreer.uk/one-facebook-pixel-code-magento-ecommerce">All-in-one Facebook Pixel Code</a> method. It&#8217;s easier to maintain.
</div>

Facebook Pixel Code is a new and even more complicated way to annoy web developers, so on top of all the Google Analytics we now have even more random JavaScript to drop into pages already growing under the weight of like and share buttons, analytics tracking, advert tracking on top of the code that actually makes the website work. Good times.

Anyhoo, this is the process for adding a successful order tracking. It all takes place on the success.phtml page or your theme so go ahead and open the file: `app\design\frontend\PACKAGE\THEME\template\checkout\success.phtml`

Facebook conversion tracking requires the order total. Add the following PHP to set the last order to an amount variable which can be reused later in the tracking code.

<pre>&lt;?php
//Get Order Number & Order Total
$order = Mage::getModel('sales/order')-&gt;loadByIncrementId(Mage::getSingleton('checkout/session')-&gt;getLastRealOrderId());
$amount = number_format($order-&gt;getGrandTotal(),2);
?&gt;</pre>

Finally, add the Facebook conversion code itself. Be sure to substitute the 100000001 below with the value form your Facebook conversion code &#8211; it appears twice in the JavaScript and the Image SRC. Also you may need to modify the currency parameter, again it appears twice.

<pre>&lt;script type="text/javascript"&gt;
var fb_param = {};
fb_param.pixel_id = '100000001';
fb_param.value = '&lt;?php echo $amount; ?&gt;';
fb_param.currency = 'GBP';
(function(){
  var fpw = document.createElement('script');
  fpw.async = true;
  fpw.src = '//connect.facebook.net/en_US/fp.js';
  var ref = document.getElementsByTagName('script')[0];
  ref.parentNode.insertBefore(fpw, ref);
})();
&lt;/script&gt;
&lt;noscript&gt;&lt;img height="1" width="1" alt="" style="display:none" src="https://www.facebook.com/offsite_event.php?id=100000001&amp;value=&lt;?php echo $amount; ?&gt;&amp;currency=GBP" /&gt;&lt;/noscript&gt;</pre>

You can now go ahead and test to confirm.