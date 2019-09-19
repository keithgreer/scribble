---
layout: home
title: Freelance Magento Web Developer - Belfast, NI | Keith Greer
h1: Keith Greer
description: Freelance Magento and WordPress website development and design in Belfast Northern Ireland, find out more.
image: https://keithgreer.uk/wp-content/uploads/2016/10/duck.png
---

> Hello, I'm Keith, web developer in Belfast working with PHP, Magento, WordPress along with everything that involves getting websites online.


## Latest Posts

{% for post in site.posts limit:1 %}
<h3><a href="{{ site.url }}{{ post.url }}" class="db pv1 link blue hover-mid-gray">
  <time class="fr silver ttu">{{ post.date | date_to_string }} </time>
  {{ post.title }}
</a></h3>
{% endfor %}
<ul class="list pa0">
{% for post in site.posts offset:1 limit:4 %}
  <li class="mv2">
    <a href="{{ site.url }}{{ post.url }}" class="db pv1 link blue hover-mid-gray">
      <time class="fr silver ttu">{{ post.date | date_to_string }} </time>
      {{ post.title }}
    </a>
  </li>
{% endfor %}
</ul>

---

## [Web Developmment](/website-development)

From custom WordPress Development to bespoke web applications and Online Leaning Environments I've worked on a range of projects and am always looking out for the next interesting project.

I offer website development based on a clear information structure that easily engages with your customers or members. My development experience includes using the most widely used programming languages on the internet including PHP and MySQL databases.

* [Running XAMPP on Ubuntu using Terminal](/running-xampp-on-ubuntu-using-terminal)
* [Jekyll Static CMS Deployments](/2019/02/jekyll)
* [Useful .gitattributes defaults for Beanstalk Git](/useful-gitattributes-defaults-for-beanstalk-git)

---

## [Magento eCommerce](/magento-ecommerce)

From custom WordPress Development to bespoke web applications and Online Leaning Environments I've worked on a range of projects and am always looking out for the next interesting project. I offer website development based on a clear information structure that easily engages with your customers or members. My development experience includes using the most widely used programming languages on the internet including PHP and MySQL databases.

* [Magento 2 Reindexer Script](/magento-2-reindex-script-indexer)
* [Magento 2 Ordering Assets](/ordering-assets-in-magento-2)
* [Magento 1 End of Life](/magento-1-end-of-life)

---

## [WordPress](/wordpress-northern-ireland)

WordPress is fast, flexible, well supported and open source. Your WordPress site site is built from the ground up to be fast, accessible and search engine friendly.

* [Why is Wordpress so popular](/why-is-wordpress-so-popular)
* [Completely disable comments using functions.php](/wordpress-code-completely-disable-comments-using-functions-php)
* [Use WordPress blog tags to find related posts](/use-wordpress-blog-tags-to-find-related-posts-php)

____


Thanks for visiting.

