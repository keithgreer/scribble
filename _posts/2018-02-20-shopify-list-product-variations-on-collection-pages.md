---
id: 1156
title: 'Shopify: List product variations on collection pages'
date: 2018-02-20T16:08:58+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1156
permalink: /shopify-list-product-variations-on-collection-pages
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
image: /cms/wp-content/uploads/2018/02/shopify.png
categories:
  - Code
tags:
  - .liquid
  - Shopify
---
The code below will allow you to display a set of product variations on a Shopify product collection pages. 

Set this code in the collections page product loop, or within the liquid snippet that controls the display of products. On line three I&#8217;ve specified &#8220;Weight&#8221; as the option I want to display so on the list page the customer can see that I have 25ml, 50ml, and 100ml product sizes available. 

<pre>{% comment %}{% for option in product.options %}
  {% if option == 'Weight' %}
    {% assign index = forloop.index0 %}
      {% for variant in product.variants %}
        {{ variant.options[index] }}
      {% endfor %}
    {% endif %}
{% endfor %}{% endcomment %}</pre>
