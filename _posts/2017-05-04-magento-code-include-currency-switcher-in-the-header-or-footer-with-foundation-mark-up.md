---
id: 937
title: 'Magento Code: Include currency switcher in the header or footer with Foundation mark-up'
date: 2017-05-04T12:21:03+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=937
permalink: /magento-code-include-currency-switcher-in-the-header-or-footer-with-foundation-mark-up
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
  - Currency
  - Foundation Framework
  - Magento
  - Magento Code
  - PHP
---
It is easy to set-up multi-currencies in Magento. This code  allows you to quickly include a currency drop down or link to  the header or footer of your Magento store. Before you begin make sure you have enabled more than one currency  as this example won’t work without at least one additional currency alongside your base currency.

Set-up the following code in your theme directory `/app/design/frontend/package/theme/template/currency/currency.phtml`. I&#8217;ve included code for both a drop down select box, or inline list of hyperlinks.

<!--more-->

## Display as a select drop-down

<pre>&lt;?php if($this-&gt;getCurrencyCount() &gt; 1): ?&gt;
&lt;div class="currency input-group"&gt;
   &lt;label class="input-group-label" for="custom-currency-selector"&gt;&lt;?php echo $this-&gt;__('Your Currency:') ?&gt;&lt;/label&gt;
   &lt;select class="input-group-field" onchange="window.location.href=this.value" name="custom-currency-selector" id="custom-currency-selector"&gt;
   &lt;?php foreach ($this-&gt;getCurrencies() as $iso =&gt; $name): ?&gt;
      &lt;option value="&lt;?php echo $this-&gt;getSwitchCurrencyUrl($iso)?&gt;" &lt;?php if($iso == $this-&gt;getCurrentCurrencyCode()): ?&gt;selected &lt;?php endif; ?&gt;&gt;
         &lt;?php echo $iso ?&gt; - &lt;?php echo $name ?&gt;
      &lt;/option&gt;
   &lt;?php endforeach; ?&gt;
   &lt;/select&gt;
   &lt;/div&gt;
&lt;?php endif; ?&gt;</pre>

## Display as an inline list of hyperlinks

<pre>&lt;?php if($this-&gt;getCurrencyCount() &gt; 1): $count = 0; ?&gt;
&lt;ul class="inline-list"&gt;
   &lt;?php foreach ($this-&gt;getCurrencies() as $iso =&gt; $name): ?&gt;
      &lt;li&gt;
         &lt;?php if($iso == $this-&gt;getCurrentCurrencyCode()): ?&gt;
            &lt;strong&gt;&lt;?php echo $iso ?&gt;&lt;/strong&gt;
         &lt;?php else: ?&gt;
            &lt;a href="&lt;?php echo $this-&gt;getSwitchCurrencyUrl($iso)?&gt;" &gt;&lt;?php echo $iso ?&gt;&lt;/a&gt;
         &lt;?php endif; ?&gt;
      &lt;/li&gt;
      &lt;?php $count++; if ( $this-&gt;getCurrencyCount() &gt; $count ) { echo " &lt;li&gt;/&lt;/li&gt;"; } ?&gt;
   &lt;?php endforeach; ?&gt;
&lt;/ul&gt;
&lt;?php endif; ?&gt;</pre>

Then include the following in your `/app/design/layout/local.xml`. The reference tag can be changed from header to footer depending on where you want to include the currency switcher on the page.

<pre>&lt;?xml version="1.0"?&gt;
&lt;layout version="0.1.0"&gt;
   &lt;default&gt;
      &lt;reference name="header"&gt;
         &lt;block type="directory/currency" name="custom_currency_selector" template="currency/currency.phtml"/&gt;
      &lt;/reference&gt;
   &lt;/default&gt;
&lt;/layout&gt;</pre>

The final step is to include the block in either `header.phtml` or `footer.phtml` as outlined above.

<pre>&lt;?php echo $this-&gt;getChildHtml('custom_currency_selector') ?&gt;</pre>