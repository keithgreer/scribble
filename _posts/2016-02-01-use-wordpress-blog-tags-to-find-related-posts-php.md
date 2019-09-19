---
id: 376
title: 'PHP: Use WordPress blog tags to find related posts'
date: 2016-02-01T15:44:52+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=376
permalink: /use-wordpress-blog-tags-to-find-related-posts-php
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
  - Notes
tags:
  - PHP
  - WordPress
---
A simple script that can be used to pull related-type posts for a WordPress blog post. The related aspect is based on the fist tag assigned to the post. The script will return at most 5 other posts from the site that also include the first tag. 

<pre class="wp-code-highlight prettyprint prettyprinted">&lt;?php

$tags = wp_get_post_tags($post-&gt;ID);

if ($tags) {
    
    $first_tag = $tags[0]-&gt;term_id;
    
    $select = array(
       'tag__in'          =&gt; array($tags[0]-&gt;term_id),
       'post__not_in'     =&gt; array($post-&gt;ID),
       'posts_per_page'   =&gt; 5,
       'caller_get_posts' =&gt; 1
    );
    
    $tag = get_tag($first_tag);
   
    $tag_query = new WP_Query($select);
   
    if( $tag_query-&gt;have_posts() ) {
        echo "&lt;ul&gt;";
        while ($tag_query-&gt;have_posts()) : $tag_query-&gt;the_post(); ?&gt;
            &lt;li&gt;
                &lt;a href="&lt;?php the_permalink() ?&gt;"&gt;
                   &lt;?php the_title(); ?&gt;
                &lt;/a&gt;
            &lt;/li&gt;

        &lt;?php endwhile;
        echo "&lt;/ul&gt;";
    }
    
    wp_reset_query();
}

?&gt;</pre>

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