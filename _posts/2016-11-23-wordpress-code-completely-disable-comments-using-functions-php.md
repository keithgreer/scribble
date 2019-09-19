---
id: 733
title: 'WordPress Code: Completely disable comments using functions.php'
date: 2016-11-23T09:48:18+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=733
permalink: /wordpress-code-completely-disable-comments-using-functions-php
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
image: /cms/wp-content/uploads/2016/02/Screen-Shot-2016-01-19-at-16.58.29.png
categories:
  - Code
tags:
  - Configuration
  - PHP
  - Website Optimisation
  - WordPress
---
The code below will completely disable any commenting and trackback features in WordPress. This code won&#8217;t turn off any &#8220;This post has X comments&#8221; or front-end code that displays comments that may be in your theme. Instead it removes the ability for comments to be added/stored against posts.

It is in response to the usual issue whereby you think comments have been completely disabled only to get a notification that there is a new comments waiting moderation.

Simply copy and paste into your `functions.php` file in your template.

<pre>// First, this will disable support for comments and trackbacks in post types
function df_disable_comments_post_types_support() {
   $post_types = get_post_types();
   foreach ($post_types as $post_type) {
      if(post_type_supports($post_type, 'comments')) {
         remove_post_type_support($post_type, 'comments');
         remove_post_type_support($post_type, 'trackbacks');
      }
   }
}
add_action('admin_init', 'df_disable_comments_post_types_support');

// Then close any comments open comments on the front-end just in case
function df_disable_comments_status() {
   return false;
}
add_filter('comments_open', 'df_disable_comments_status', 20, 2);
add_filter('pings_open', 'df_disable_comments_status', 20, 2);

// Finally, hide any existing comments that are on the site. 
function df_disable_comments_hide_existing_comments($comments) {
   $comments = array();
   return $comments;
}
add_filter('comments_array', 'df_disable_comments_hide_existing_comments', 10, 2);</pre>

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