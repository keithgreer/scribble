---
id: 624
title: 'Quickfix: Quickly add a new Magento CMS page template'
date: 2016-07-21T11:13:03+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=624
permalink: /quickfix-quickly-add-new-magento-cms-page-template
colour:
  - blog
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
  - Quickfix
---
Sometimes it&#8217;s necessary to quickly add a template for a page into the Magento content management system. This can be done via a custom extension below is the quick fix if required.

Find the closing global tag `</global>` and add the following code above it. It will add two templates one from homepage.phtml and one for another-page.html which can then be set on the Design Tab in CMS > Pages.

<pre><span style="color: #999999;">&lt;global&gt;</span>
    &lt;cms&gt;
        &lt;layouts&gt;
            &lt;homepage&gt;
                &lt;label&gt;Homepage&lt;/label&gt;
                &lt;template&gt;page/homepage.phtml&lt;/template&gt;
            &lt;/homepage&gt;
            &lt;another_page&gt;
                &lt;label&gt;Abother Page&lt;/label&gt;
                &lt;template&gt;page/another-page.phtml&lt;/template&gt;
            &lt;/another_page&gt;
        &lt;/layouts&gt;
    &lt;/cms&gt;
<span style="color: #999999;">&lt;/global&gt;</span></pre>