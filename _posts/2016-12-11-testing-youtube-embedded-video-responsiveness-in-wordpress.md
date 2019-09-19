---
id: 858
title: Testing YouTube embedded video responsiveness in WordPress
date: 2016-12-11T03:12:41+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=858
permalink: /testing-youtube-embedded-video-responsiveness-in-wordpress
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
  - Notes
tags:
  - Embed
  - Video
  - WordPress
  - YouTube
---
It turns out YouTube video uploads have come a long way since I last tried them out. This is a test post with no discernibly interesting content. WordPress has, for quite a long time allowed embedding YouTube content simply by copy and pasting the URL into the WordPress post editor.



Checking-out how WordPress handles YouTube embeds, whether or not they are responsive and if not how I can make them work better.

## Update

So it turned out that the standard embed method will add a fixed width video iframe into the page. To make this responsive a couple of additions were required.

First wrap YouTube embed iframes in a container. Add the following script to your theme `functions.php` script

<pre>add_filter('embed_oembed_html', 'wrap_embed_with_div', 10, 3);

function wrap_embed_with_div($html, $url, $attr) {
    return "&lt;div class=\"responsive-container\"&gt;".$html."&lt;/div&gt;";
}</pre>

Then add a little bit of CSS to your themes `style.css` or wherever your main CSS file is

<pre>.responsive-container { position: relative; padding-bottom: 50.25%; padding-top: 30px; height: 0; overflow: hidden; margin-bottom: 1em; }
.responsive-container iframe { position: absolute; top: 0; left: 0; width: 100%; height: 100%;}</pre>

And that did the job.

* * *

<div class="row">
  <div class="column large-6 medium-6 small-12">
    <h2>
      WordPress developer
    </h2>
    
    <p>
      in Belfast, Northern Ireland
    </p>
  </div>
  
  <div class="column large-6 medium-6 small-12">
    <p>
      I&#8217;ve been developing WordPress websites for 10 years and am always looking for the next exciting project from personal blog, community portal or business website. Why not get in touch to see if I can help you with yours.
    </p>
    
    <p>
      <a class="button" href="/contact">Contact me today!</a>
    </p>
  </div>
</div>