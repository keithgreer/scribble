---
id: 523
title: 'Cloudflare: My next step for website optomisation'
date: 2016-03-25T16:30:31+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=523
permalink: /cloudflare-my-next-step-for-website-optomisation
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
  - CloudFlare
  - Content Delivery Networks
  - Website Optimisation
---
I&#8217;ve been working to dramatically reduce page load times on my site. Load times were reduced from 6 seconds to about 3 just by minifying content, using a CDN for static resources and generally removing scripts images that were not required.

My main issues ended up being a slow server using cheap hosting and an SSL certificate that marginally increases the download time.

[<img class="alignnone size-full wp-image-525 aligncenter" src="https://keithgreer.uk/cms/wp-content/uploads/2016/03/with-cloudflare.png" alt="with-cloudflare" width="619" height="319" srcset="https://keithgreer.uk/cms/wp-content/uploads/2016/03/with-cloudflare.png 619w, https://keithgreer.uk/cms/wp-content/uploads/2016/03/with-cloudflare-300x155.png 300w" sizes="(max-width: 619px) 100vw, 619px" />](https://keithgreer.uk/cms/wp-content/uploads/2016/03/with-cloudflare.png)

The load times of just under 2 seconds were achieved

[<img class="aligncenter size-large wp-image-524" src="https://keithgreer.uk/cms/wp-content/uploads/2016/03/with-cloudflare-settings-for-wordpress.png" alt="with-cloudflare-settings-for-wordpress" width="640" height="164" srcset="https://keithgreer.uk/cms/wp-content/uploads/2016/03/with-cloudflare-settings-for-wordpress.png 685w, https://keithgreer.uk/cms/wp-content/uploads/2016/03/with-cloudflare-settings-for-wordpress-300x77.png 300w" sizes="(max-width: 640px) 100vw, 640px" />](https://keithgreer.uk/cms/wp-content/uploads/2016/03/with-cloudflare-settings-for-wordpress.png)

The above rules were required in CloudFlare to get it working correctly with WordPress, the first rule turns off caching for the admin area and a few other bits and pieces. The second rule ensures page preview works. Both these rules completely do away with caching at all levels.

The last rule is the catch all for everything not included in the above two rules. it caches everything on the domain.

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