---
id: 723
title: 'MySQL TRUNCATE command: Quickly and easilty clear out the Magento database'
date: 2016-11-22T17:16:51+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=723
permalink: /mysql-truncate-command-quickly-and-easilty-clear-out-the-magento-database
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
image: /cms/wp-content/uploads/2016/02/mysql.png
categories:
  - Code
tags:
  - Magento
  - Magento Code
  - MySQL
---
This is a simple list of SQL commands which can be used to clear out various parts of the Magento database. It&#8217;ll be useful when creating a development environment from an existing database. It will clear all real customer, orders and sales data while keeping the catalogue and CMS information. 

The basic command should be to disable foreign key checks in MySQL, followed by the required truncate commands, then reenable foreign key checks. 

<pre>SET FOREIGN_KEY_CHECKS=0; </pre>

**Clear the log tables down**

This should be managed by Magento but issues with Cron scheduling can mean they grow way beyond a reasonable size. Clearing the log tables will have no impact on the system. 

<pre>TRUNCATE `log_customer`; 
TRUNCATE `log_quote`; 
TRUNCATE `log_summary`; 
TRUNCATE `log_summary_type`; 
TRUNCATE `log_url`; 
TRUNCATE `log_url_info`; 
TRUNCATE `log_visitor`; 
TRUNCATE `log_visitor_info`; 
TRUNCATE `log_visitor_online`; </pre>

**Clear out report tables**

The report tables will, again, have no negative impact on your store but it will affect performance of some features including recently viewed products, and any reporting you do will need rebuilt before run again. 

<pre>TRUNCATE `coupon_aggregated`;
TRUNCATE `coupon_aggregated_order`;
TRUNCATE `coupon_aggregated_updated`;
TRUNCATE `report_viewed_product_aggregated_daily`;
TRUNCATE `report_viewed_product_aggregated_monthly`;
TRUNCATE `report_viewed_product_aggregated_yearly`;
TRUNCATE `sales_bestsellers_aggregated_daily`;
TRUNCATE `sales_bestsellers_aggregated_monthly`;
TRUNCATE `sales_bestsellers_aggregated_yearly`;
TRUNCATE `sales_invoiced_aggregated`;
TRUNCATE `sales_invoiced_aggregated_order`;
TRUNCATE `sales_order_aggregated_created`;
TRUNCATE `sales_order_aggregated_updated`;
TRUNCATE `sales_refunded_aggregated`;
TRUNCATE `sales_refunded_aggregated_order`;
TRUNCATE `sales_shipping_aggregated`;
TRUNCATE `sales_shipping_aggregated_order`;
TRUNCATE `tax_order_aggregated_created`;
TRUNCATE `tax_order_aggregated_updated`;</pre>

Miscellaneous

<pre>TRUNCATE `catalogsearch_query`;
TRUNCATE `index_event`; 
TRUNCATE `index_process_event`;   
TRUNCATE `report_event`;
TRUNCATE `report_viewed_product_index`;
TRUNCATE `sendfriend_log`; 
TRUNCATE `tag`; 
TRUNCATE `tag_relation`; 
TRUNCATE `tag_summary`; 
TRUNCATE `wishlist`;</pre>

Remove customer information

<pre>-- Customerc
TRUNCATE `customer_entity`;
TRUNCATE `customer_entity_datetime`;
TRUNCATE `customer_entity_decimal`;
TRUNCATE `customer_entity_int`;
TRUNCATE `customer_entity_text`;
TRUNCATE `customer_entity_varchar`;

-- Customer Addresses
TRUNCATE `customer_address_entity`;
TRUNCATE `customer_address_entity_datetime`;
TRUNCATE `customer_address_entity_decimal`;
TRUNCATE `customer_address_entity_int`;
TRUNCATE `customer_address_entity_text`;
TRUNCATE `customer_address_entity_varchar`;</pre>

Sales Quotes and Order Data

<pre>-- Quotes
TRUNCATE `sales_flat_quote`; 
TRUNCATE `sales_flat_quote_address`; 
TRUNCATE `sales_flat_quote_address_item`; 
TRUNCATE `sales_flat_quote_item`; 
TRUNCATE `sales_flat_quote_item_option`; 
TRUNCATE `sales_flat_quote_payment`; 
TRUNCATE `sales_flat_quote_shipping_rate`; 

-- Orders
TRUNCATE `sales_flat_order`; 
TRUNCATE `sales_flat_order_address`; 
TRUNCATE `sales_flat_order_grid`; 
TRUNCATE `sales_flat_order_item`; 
TRUNCATE `sales_flat_order_payment`; 
TRUNCATE `sales_flat_order_status_history`;

-- Invoices
TRUNCATE `sales_flat_invoice`;
TRUNCATE `sales_flat_invoice_comment`;
TRUNCATE `sales_flat_invoice_grid`;
TRUNCATE `sales_flat_invoice_item`;

-- Shipments
TRUNCATE `sales_flat_shipment`;
TRUNCATE `sales_flat_shipment_comment`;
TRUNCATE `sales_flat_shipment_grid`;
TRUNCATE `sales_flat_shipment_item`;
TRUNCATE `sales_flat_shipment_track`;

-- Sales Order Tax
TRUNCATE `sales_order_tax`;
TRUNCATE `sales_order_tax_item`;

-- Creditmemos
TRUNCATE `sales_flat_creditmemo`;
TRUNCATE `sales_flat_creditmemo_comment`;
TRUNCATE `sales_flat_creditmemo_grid`;
TRUNCATE `sales_flat_creditmemo_item`;</pre>

After each update, re-enable foreign key checks. 

<pre>SET FOREIGN_KEY_CHECKS=1;</pre>