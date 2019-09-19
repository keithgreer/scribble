---
id: 308
title: Setting up your Magento Store to cope with that Black Friday surge
date: 2015-11-27T10:02:53+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=308
permalink: /setting-up-your-magento-store-to-cope-with-a-black-friday-surge
colour:
  - green
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
image: /cms/wp-content/uploads/2015/11/magento-generic.png
categories:
  - Userguide
tags:
  - Caching
  - Configuration
  - Magento
  - Userguide
  - Website Optimisation
---
These are a few simple Magento store configuration options that can help your store cope with increased traffic during Black Friday or any sort of high traffic period.

Realistically all of these should not be run on a production environment before first testing them properly. Best to get these in place before those promotions and discounts go live.

**Enable & refresh all caches** (System > Cache Management)

Most people will be familiar with clearing their Magento cache or refreshing one of the options. Clearing your cache will generate fresh copies of your catalogue.

**Disable logging** (System > Configuration > Developer > Log Settings)

Logging is used to monitor problems on your website, this can include errors processing payments or issues with extensions. Typically it won&#8217;t cause any issues but during high traffic periods it is a features that just adds to the length of time it takes to process requests.

**Enable flat catalogue categories/products** (System > Configuration > Catalogue > Frontend)

Flat catalogue is useful _only_ on websites which don&#8217;t have a lot of their own custom attributes associated with products. But will work best if you only use the standard product attributes which come with Magento.

**Enable compilation** (System > Tools > Compilation)

Be careful with this one as it can crash your store. It will be available on stores from version 1.3.2+. Disable cache first and if everything works fine you can re-enable the caching from. Speed improvements will depend on the size of your Magento install.

* * *

<div class="row">
  <div class="column large-6 medium-6 small-12">
    <h2>
      Magento developer
    </h2>
    
    <p>
      in Belfast, Northern Ireland
    </p>
  </div>
  
  <div class="column large-6 medium-6 small-12">
    <p>
      I&#8217;ve been developing <a href="https://keithgreer.uk/magento-ecommerce">Magento</a> websites in Northern Ireland for over 7 years and am always looking for the next exciting ecommerce project. Why not get in touch to see if I can help you with yours.
    </p>
    
    <p>
      <a class="button" href="/contact">Contact me today!</a>
    </p>
  </div>
</div>