---
id: 978
title: 'Magento: What are Sage Pay Orphan Transactions?'
date: 2017-06-06T09:29:01+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=978
permalink: /magento-sage-pay-orphan-transactions
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
image: /cms/wp-content/uploads/2017/06/orphan-transactions.png
categories:
  - Notes
tags:
  - Configuration
  - Magento
  - Magento Issues
  - Sage Pay
---
<img class="alignnone size-full wp-image-981" src="http://keithgreer.uk/cms/wp-content/uploads/2017/06/orphan-transactions.png" alt="" width="1435" height="773" srcset="https://keithgreer.uk/cms/wp-content/uploads/2017/06/orphan-transactions.png 1435w, https://keithgreer.uk/cms/wp-content/uploads/2017/06/orphan-transactions-300x162.png 300w, https://keithgreer.uk/cms/wp-content/uploads/2017/06/orphan-transactions-768x414.png 768w, https://keithgreer.uk/cms/wp-content/uploads/2017/06/orphan-transactions-1024x552.png 1024w" sizes="(max-width: 1435px) 100vw, 1435px" />

This is a regular issue when using Sage Pay with Magento that needs a bit of explaining.

Sage Pay transactions started by the customer are stored in the Magento database. When a transaction is completed successfully this Sage Pay transaction is linked to the completed order in Magento.

When a order does not complete this leaves transactions in the Magento database not connected to a Magento order ID. These are orphaned transactions. The cause can be the customer abandoning the order at some point (e.g. the 3D secure checks), a declined/rejected payment, or caused by an error when Magento Saves the order. Because there is no completed Order ID to connect the transaction to these are considered &#8220;orphans&#8221;.

Orphaned  transactions are not always bad. If you monitor the list of orphaned transactions in Magneto (Sales > Sage Pay > Orphan Transactions) you can use the details to recover lost sales, for example a telephone or email address may be available to contact customers who have been unable to complete 3D Security checks and enter the order manually.

The most important thing to note is that Sage Pay integration will not tell Magento to save an order unless the payment has been successfully taken. The successful payment response from Sage Pay will create the &#8220;processing&#8221; order in Magento. This stops issues with inventory and shipping unpaid for orders.

The Sage Pay Suite Orphan Transaction list will not only help you spot issues with customers processing orders, it can also help you recover sales.