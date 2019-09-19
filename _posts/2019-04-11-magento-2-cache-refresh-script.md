---
title: 'Magento Code: Magento 2 Cache Refresh Script'
date: 2019-04-11T11:00:00+00:00
image: "https://keithgreer.uk/wp-content/uploads/2016/02/magento-generic.png"
author: Keith Greer
layout: post
permalink: /magento-2-cache-refresh-script
---

This is a stand alone script which can be called to refresh the cache in Magento 2

<script src="https://gist.github.com/keithgreer/1121f6a08ad6033272dd21274159eac8.js"></script>

The script hooks into Bootstrap to generate a unique instance without needing to hook into Magento itself. The System will loop through all the cache types specified on line 13. If you have any custom modules that also require a cache, add it into this list. 

