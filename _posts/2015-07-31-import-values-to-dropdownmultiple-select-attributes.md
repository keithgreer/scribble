---
id: 184
title: Import Values to Dropdown/Multiple Select Attributes
date: 2015-07-31T09:24:44+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=184
permalink: /import-values-to-dropdownmultiple-select-attributes
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
  - Magento Code
  - PHP
---
Sometime when you need to deal with import of lots of values for a multiple select/drop down attribute. Then manual data entry is not very convenient. The code below will allow you to put all your values into a single text file and import in seconds. First you will need to upload the source code below into a new file manufacturer_import.php in the Magento root directory.

<!--more-->

<pre class="wp-code-highlight prettyprint prettyprinted"><span class="pun">&lt;?</span><span class="pln">php
require_once </span><span class="str">'../app/Mage.php'</span><span class="pun">;</span><span class="pln">
umask</span><span class="pun">(</span><span class="lit"></span><span class="pun">);</span><span class="typ">Mage</span><span class="pun">::</span><span class="pln">app</span><span class="pun">(</span><span class="str">'default'</span><span class="pun">);</span><span class="pln">
$_manufacturers </span><span class="pun">=</span><span class="pln"> file</span><span class="pun">(</span><span class="str">'import.txt'</span><span class="pun">);</span><span class="pln">
$_attribute </span><span class="pun">=</span><span class="typ">Mage</span><span class="pun">::</span><span class="pln">getModel</span><span class="pun">(</span><span class="str">'eav/entity_attribute'</span><span class="pun">)-&gt;</span><span class="pln">loadByCode</span><span class="pun">(</span><span class="str">'catalog_product'</span><span class="pun">,</span><span class="str">'manufacturer'</span><span class="pun">);</span><span class="pln">
$manufacturers </span><span class="pun">=</span><span class="pln"> array</span><span class="pun">(</span><span class="str">'value'</span><span class="pun">=&gt;</span><span class="pln"> array</span><span class="pun">(),</span><span class="str">'order'</span><span class="pun">=&gt;</span><span class="pln"> array</span><span class="pun">(),</span><span class="str">'delete'</span><span class="pun">=&gt;</span><span class="pln"> array</span><span class="pun">());</span><span class="pln">
$i </span><span class="pun">=</span><span class="lit"></span><span class="pun">;</span><span class="kwd">foreach</span><span class="pun">(</span><span class="pln">$_manufacturers </span><span class="kwd">as</span><span class="pln"> $_manufacturer</span><span class="pun">){</span><span class="pln">
    $i</span><span class="pun">++;</span><span class="pln">
    $manufacturers</span><span class="pun">[</span><span class="str">'value'</span><span class="pun">][</span><span class="str">'option_'</span><span class="pun">.</span><span class="pln"> $i</span><span class="pun">]</span><span class="pun">=</span><span class="pln"> array</span><span class="pun">(</span><span class="pln">$_manufacturer</span><span class="pun">);</span><span class="pun">}</span><span class="pln">
$_attribute</span><span class="pun">-&gt;</span><span class="pln">setOption</span><span class="pun">(</span><span class="pln">$manufacturers</span><span class="pun">);</span><span class="kwd">try</span><span class="pun">{</span><span class="pln">
    $_attribute</span><span class="pun">-&gt;</span><span class="pln">save</span><span class="pun">();</span><span class="pln">
    echo </span><span class="str">'Attribute values successfully imported'</span><span class="pun">;</span><span class="pun">}</span><span class="kwd">catch</span><span class="pun">(</span><span class="typ">Exception</span><span class="pln"> $e</span><span class="pun">){</span><span class="pln">
    echo </span><span class="str">'Import Error::'</span><span class="pun">.</span><span class="pln">$e</span><span class="pun">-&gt;</span><span class="pln">getMessage</span><span class="pun">();</span><span class="pun">}</span></pre>

The above code will import Manufacturers into the “manufacturer” attribute, but can be used on any drop-down or multiple select attribute configured in Magento, simply change “manufacturer” at the end of line 6 to the code of the attribute you wish to update.

Next step is to prepare and upload your list of manufactures in a simple text file, one value per line. Save the file as “import.txt”, and upload into Magento root directory, beside the above script.

<pre class="wp-code-highlight prettyprint prettyprinted">Apple
Banana
Pear
...</pre>

Navigate to www.magento.com/manufacturer_import.php and you sould see the import successful message.

Source: [http://www.magentocommerce.com/wiki/](http://www.magentocommerce.com/wiki/3_-_store_setup_and_management/import_export/import_manufacturers)