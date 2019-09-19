---
title: 'Magento Code: Magento 2 Indexer Script'
date: 2019-04-11T10:00:00+00:00
image: "https://keithgreer.uk/wp-content/uploads/2016/02/magento-generic.png"
author: Keith Greer
layout: post
permalink: /magento-2-reindex-script-indexer
---

This is a stand alone script which can be called to reindex a Magento 2 Site

<script src="https://gist.github.com/keithgreer/9534645a7ba18e82dd227ec31b340ba5.js"></script>

The script will create a unique instance of the Magento Object Manager and use it to loop through all the indexes in the registry. You shouldn't need to modify the script for any third party indexes that may be added by modules, as long as they have been properly registered. 

