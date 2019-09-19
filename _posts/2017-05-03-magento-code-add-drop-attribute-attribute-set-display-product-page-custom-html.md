---
id: 930
title: 'Magento Code: Add a drop down attribute and display it on the product page in custom HTML'
date: 2017-05-03T09:19:48+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=930
permalink: /magento-code-add-drop-attribute-attribute-set-display-product-page-custom-html
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
  - Magento
  - Magento Code
  - PHP
---
Magento makes it really easy to expand the usual product attributes through the Admin Panel. While these can be added to the product page in the standard attribute list table, you may want your attribute to appear differently or use it for another feature. This post explains how.

In this example we&#8217;ll be adding an attribute to tell the customer how long they might have to wait on a product to arrive.

## <!--more-->Create a new Attribute

Click into Catalog > Attributes > Manage Attributes. Click on **Add New Attribute**

  * Attribute Code:  **delivery\_lead\_time**
  * Scope: **Global** (this means the value of the attribute will be shared across store views if applicable)
  * Catalog Input Type for Store Owner: **Dropdown**

The other values can be left as default. Next click into the Manage Label/Options tab

Set the value for &#8220;admin&#8221; to be the human readable form or the attribute name &#8220;Delivery Lead Time&#8221;, then below add the options that you want to display&#8230;

<pre><img class="alignnone size-full wp-image-931" src="http://keithgreer.uk/cms/wp-content/uploads/2017/05/delivery-lead-time-2.png" alt="" width="926" height="386" srcset="https://keithgreer.uk/cms/wp-content/uploads/2017/05/delivery-lead-time-2.png 926w, https://keithgreer.uk/cms/wp-content/uploads/2017/05/delivery-lead-time-2-300x125.png 300w, https://keithgreer.uk/cms/wp-content/uploads/2017/05/delivery-lead-time-2-768x320.png 768w" sizes="(max-width: 926px) 100vw, 926px" /></pre>

### Update the attribute set

In Catalog > Attributes > Manage Attribute Sets click into the attribute set (oftentimes the one labelled &#8220;Default&#8221;).

The new attribute will be listed in the &#8220;Unassigned Attributes&#8221; section on the right hand side of the page. Drag and drop your attribute into the Groups column in the middle of the page. These groups are the tabbed sections that appear on the product edit view. Once you have placed and ordered your new attribute click **Save Attribute**.

### Update the product

Your new attribute will now appear in the product edit view, depending on where it was placed in the attribute set.

It will also be available to update through the batch product editor.

## Add the new attribute to the front end

The attribute can then be loaded onto the product page using the following code. First check if the attribute has been set, if it has add the value into a container.

<pre>&lt;?php if  ($_product-&gt;getAttributeText('delivery_lead_time')): ?&gt;
    &lt;div class="lead-time"&gt;&lt;?php echo $_product-&gt;getAttributeText('delivery_lead_time'); ?&gt;&lt;div&gt;
&lt;?php endif; ?&gt;</pre>