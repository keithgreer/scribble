---
id: 1084
title: Checkout problems upgrading to Magento 1.9.3.4+
date: 2017-10-10T08:22:38+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1084
permalink: /checkout-problems-upgrading-to-magento-1-9-3-4
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
categories:
  - Code
tags:
  - Magento Code
  - Magento Issues
  - Security
---
Magento version 1.9.3.4 include patch [SUPEE-9767 V2](https://www.sonassi.com/blog/patching-supee-9767-v2) which includes security patching for the checkout process.

For your current front-end templates to work with this patch you will need to include a form key value to a number of forms in the checkout process.

<pre>&lt;?php echo $this-&gt;getBlockHtml('formkey') ?&gt;</pre>

Load the templates below from your  `app/design/frontend/<package>/<theme>` directory and add the Form Key code above between the `<form>` and `</form>` tags on each.

The basic templates that will need upgraded:

  * `/template/checkout/cart/shipping.phtml`
  * `/template/checkout/onepage/billing.phtml`
  * `/template/checkout/onepage/shipping.phtml`
  * `/template/checkout/onepage/payment.phtml`

If persistant checkout is enabled:

  * `/template/checkout/onepage/shipping_method.phtml`
  * `/template/persistent/checkout/onepage/billing.phtml`

If you allow shippinng to multiple addresses:

  * `/template/checkout/multishipping/billing.phtml`
  * `/template/checkout/multishipping/shipping.phtml`