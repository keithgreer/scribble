---
id: 997
title: 'Magento Code: Innoexts Currency Pricing Module Price and Special Price Import via SSH'
date: 2017-06-26T13:21:37+00:00
author: Keith Greer
layout: post
permalink: /magento-code-innoexts-currency-pricing-modul-price-and-special-price-import-via-ssh
---
Magento Code: Innoexts Currency Pricing Modul Price and Special Price Imports vis SSH

## Standard Price Import 

Use the following command: 

<pre>`php /home/var/public/html/magento/shell/Innoexts/CurrencyPricing/Catalog/Product/Price/Compound/Import.php --file-path /var/import/ --file-filename standard_price.csv`</pre>

The CSV file should look something like this: 

<pre>"sku","_store","price","currency"
"SKU001","admin","55.00","EUR"</pre>

## Special Price Import

<pre>`php /home/var/public/html/magento/shell/Innoexts/CurrencyPricing/Catalog/Product/Price/CompoundSpecial/Import.php --file-path /var/import/ --file-filename special_price.csv`</pre>

The CSV file should look like the below. Don&#8217;t use &#8220;special_price&#8221; column heading in Special Price import, just &#8220;price&#8221;

<pre>sku,price,currency
SKU001,29.99,EUR</pre>
