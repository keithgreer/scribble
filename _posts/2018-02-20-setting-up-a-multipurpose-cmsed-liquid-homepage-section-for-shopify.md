---
id: 1159
title: 'Shopify: Setting up a multipurpose CMSed liquid homepage section'
date: 2018-02-20T17:08:46+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1159
permalink: /setting-up-a-multipurpose-cmsed-liquid-homepage-section-for-shopify
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
Setting up a multipurpose CMSed liquid homepage section for Shopify.

The below schema includes two sets of data

  1. A YouTube Video display
  2. A list of testimonials (max 5)

<pre>{% raw  %}{% schema %}
  {
    "name": "Video & Testimonial",
    "max_blocks": 5,
  	"settings": [
		{
          "id": "video_title",
          "type": "text",
          "label": "Heading",
          "default": "Learn 'How to' with our video"
		},
		{
          "id": "video_sub",
          "type": "text",
          "label": "Heading",
          "default": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed incididunt. Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod"
		},
		{
          "id": "video_code",
          "type": "text",
          "label": "YouTube Code",
          "default": "GF60Iuh643I"
		},
		{
          "id": "video_image",
          "type": "image_picker",
          "label": "Background Image"
		}
  	],
  	"blocks": [
      {
        "type": "testimonial",
        "name": "Testimonial Option",
        "settings": [
          {
            "id": "testimonial_subject",
            "type": "text",
            "label": "Testimonial Subject"
      	  },
          {
            "type": "image_picker",
            "id": "image",
            "label": "Image"
          },
          {
            "id": "testimonial_desc",
            "type": "textarea",
            "label": "Testimonial Description"
          },
          {
            "id": "testimonial_author",
            "type": "text",
            "label": "Testimonial Author"
          }
        ]
      }
      
    ],
    "presets": [
      {
        "name": "Video and Testimonial",
        "category": "Testimonial",
		    "settings": {}
      }
    ]
  }
{% endschema %}{% endraw %}</pre>

First we grab and display the variables from the Settings section of the JSON

<pre>{% raw %}&lt;div class="medium-6 columns"&gt;
	&lt;div class="content-wrap"&gt;
		&lt;h3&gt;&lt;span class="subheading"&gt;Learn 'How to' with our&lt;/span&gt;{{ section.settings.video_title }}&lt;/h3&gt;
		&lt;p&gt;{{ section.settings.video_sub }}&lt;/p&gt;
		&lt;a data-fancybox href="https://www.youtube.com/watch?v={{ section.settings.video_code }}" class="button"&gt;View Video&lt;/a&gt;
	&lt;/div&gt;
&lt;/div&gt;
&lt;div class="medium-6 columns"&gt;
	&lt;a data-fancybox class="image-wrap" href="https://www.youtube.com/watch?v={{ section.settings.video_code }}"&gt;
		&lt;img class="play-button" src="//cdn.shopify.com/s/files/1/2602/4064/t/2/assets/play-button.png"&gt;
		&lt;img src="{{ section.settings.video_image | img_url }}"&gt;
	&lt;/a&gt;
&lt;/div&gt;{% endraw %}</pre>

Then we grab the repeating testimonial blocks

<pre>{% raw %}{% if section.blocks.size &gt; 0 %}
&lt;section class="testimonial1 angle-bigarrow"&gt;
	&lt;div class="row"&gt;
		&lt;div class="small-12 column"&gt;
			&lt;ul class="grid-1 wow fadeInUp"&gt;
				{% for block in section.blocks %}
				&lt;li {{ block.shopify_attributes }}&gt;
					&lt;div class="testimonial-inner"&gt;
						&lt;img src="{{ block.settings.image | img_url: '150x150' }}" alt="slider" /&gt;
						&lt;h5&gt;{{ block.settings.testimonial_author }}&lt;/h5&gt;
						&lt;p&gt;{{ block.settings.testimonial_desc }}&lt;/p&gt;
					&lt;/div&gt;
				&lt;/li&gt;
				{% endfor %}
			&lt;/ul&gt;
		&lt;/div&gt;
	&lt;/div&gt;
&lt;/section&gt;
{% endif %}{% endraw %}</pre>

&nbsp;
