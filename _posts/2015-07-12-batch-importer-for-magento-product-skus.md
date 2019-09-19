---
id: 186
title: Batch importer for Magento Product SKUs
date: 2015-07-12T09:25:40+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=186
permalink: /batch-importer-for-magento-product-skus
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
  - CSV
  - Import
  - Magento
  - Magento Code
  - PHP
---
Place the following script in your Magento root folder

First create your CSV with the old and new SKU numbers in a simple CSV file as follows and upload onto FTP into the magento/var/import directory.

<!--more-->

<pre class="wp-code-highlight prettyprint prettyprinted"><span class="lit">1232</span><span class="pun">,</span><span class="kwd">new</span><span class="pun">-</span><span class="lit">24B8</span>
<span class="lit">442</span><span class="pun">,</span><span class="lit">2w39489</span>
<span class="lit">0909d</span><span class="pun">,</span><span class="lit">11299033</span></pre>

One product on each line the current SKU followed by a comma, then the new SKU you wanto to use followed by a new line. Next, place the following script in the root folder of your Magento install. Make sure `$updates_file` matches the location of the CSV file on the server.

<pre class="wp-code-highlight prettyprint prettyprinted"><span class="pun">&lt;?</span><span class="pln">php

ini_set</span><span class="pun">(</span><span class="str">'error_reporting'</span><span class="pun">,</span><span class="pln"> E_ALL</span><span class="pun">);</span>

<span class="com">// Location of Mage.php relative to current script</span><span class="pln">
include_once </span><span class="str">'app/Mage.php'</span><span class="pun">;</span>
<span class="typ">Mage</span><span class="pun">::</span><span class="pln">app</span><span class="pun">();</span>

<span class="com">// Location of CSV relative to file system root</span><span class="pln">
$updates_file</span><span class="pun">=</span><span class="str">"/magento/var/import/sku2sku.csv"</span><span class="pun">;</span><span class="pln">
$sku_entry</span><span class="pun">=</span><span class="pln">array</span><span class="pun">();</span><span class="pln">
echo realpath</span><span class="pun">(</span><span class="pln">dirname</span><span class="pun">(</span><span class="pln">__FILE__</span><span class="pun">));</span><span class="pln">
$updates_handle</span><span class="pun">=</span><span class="pln">fopen</span><span class="pun">(</span><span class="pln">$updates_file</span><span class="pun">,</span> <span class="str">'r'</span><span class="pun">);</span><span class="pln">
echo </span><span class="str">"1 "</span><span class="pun">;</span> 
<span class="kwd">if</span><span class="pun">(</span><span class="pln">$updates_handle</span><span class="pun">)</span> <span class="pun">{</span><span class="pln"> 
echo </span><span class="str">"2 "</span><span class="pun">;</span> 
    <span class="kwd">while</span><span class="pun">(</span><span class="pln">$sku_entry</span><span class="pun">=</span><span class="pln">fgetcsv</span><span class="pun">(</span><span class="pln">$updates_handle</span><span class="pun">,</span> <span class="lit">1000</span><span class="pun">,</span> <span class="str">","</span><span class="pun">))</span> <span class="pun">{</span><span class="pln"> 
        $old_sku</span><span class="pun">=</span><span class="pln">$sku_entry</span><span class="pun">[</span><span class="lit"></span><span class="pun">];</span><span class="pln">
        $new_sku</span><span class="pun">=</span><span class="pln">$sku_entry</span><span class="pun">[</span><span class="lit">1</span><span class="pun">];</span><span class="pln">
        echo </span><span class="str">"Updating "</span><span class="pun">.</span><span class="pln">$old_sku</span><span class="pun">.</span><span class="str">" to "</span><span class="pun">.</span><span class="pln">$new_sku</span><span class="pun">.</span><span class="str">" - "</span><span class="pun">;</span>
        <span class="kwd">try</span> <span class="pun">{</span><span class="pln">
            $get_item </span><span class="pun">=</span> <span class="typ">Mage</span><span class="pun">::</span><span class="pln">getModel</span><span class="pun">(</span><span class="str">'catalog/product'</span><span class="pun">)-&</span><span class="pln">gt</span><span class="pun">;</span><span class="pln">loadByAttribute</span><span class="pun">(</span><span class="str">'sku'</span><span class="pun">,</span><span class="pln"> $old_sku</span><span class="pun">);</span>
            <span class="kwd">if</span> <span class="pun">(</span><span class="pln">$get_item</span><span class="pun">)</span> <span class="pun">{</span><span class="pln">
                $get_item</span><span class="pun">-&</span><span class="pln">gt</span><span class="pun">;</span><span class="pln">setSku</span><span class="pun">(</span><span class="pln">$new_sku</span><span class="pun">)-&</span><span class="pln">gt</span><span class="pun">;</span><span class="pln">save</span><span class="pun">();</span><span class="pln">
                echo </span><span class="str">"successful"</span><span class="pun">;</span>
            <span class="pun">}</span> <span class="kwd">else</span> <span class="pun">{</span><span class="pln">
                echo </span><span class="str">"item not found"</span><span class="pun">;</span>
            <span class="pun">}</span>
        <span class="pun">}</span> <span class="kwd">catch</span> <span class="pun">(</span><span class="typ">Exception</span><span class="pln"> $e</span><span class="pun">)</span> <span class="pun">{</span><span class="pln"> 
            echo </span><span class="str">"Cannot retrieve products from Magento: "</span><span class="pun">.</span><span class="pln">$e</span><span class="pun">-&</span><span class="pln">gt</span><span class="pun">;</span><span class="pln">getMessage</span><span class="pun">().</span><span class="str">"
"</span><span class="pun">;</span>
            <span class="kwd">return</span><span class="pun">;</span>
        <span class="pun">}</span>
    <span class="pun">}</span>
<span class="pun">}</span><span class="pln">
fclose</span><span class="pun">(</span><span class="pln">$updates_handle</span><span class="pun">);</span></pre>

An [alternative method](http://www.magentocommerce.com/wiki/import-export_and_data_manipulation/update_skus_with_dataflow_en-masse_from_a_.csv_file) uses the SOAP API built into Magento but is slightly slower.