---
id: 671
title: How to use PHP to submit a cURL request with HTTP Post data
date: 2016-10-28T15:01:24+00:00
author: Keith Greer
layout: post
guid: https://keithgreer.uk/?p=671
permalink: /how-to-use-php-to-submit-a-curl-request-with-http-post-data
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
image: /cms/wp-content/uploads/2016/10/duck.png
categories:
  - Code
tags:
  - cURL
  - PHP
---
Straight forward script to POST an array of fields to a given URL.

<pre>// First, set the URL you want to POST the data to
$url = 'http://domain.com/script/';

// Specify the POST data
$fields = array(
  'field1' =&gt; "Value 1",
  'field2' =&gt; "Value Two",
  'field3' =&gt;  "Value 3"
);


// Next, erge the array data into a single sting
foreach ($fields as $key =&gt; $value) { $fields_string .= $key . '=' . $value . '&'; }
$fields_string = "";
rtrim($fields_string, '&');

// Open a CURL connection
$ch = curl_init();

// Set the CURL options
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_POST, count($fields));
curl_setopt($ch, CURLOPT_POSTFIELDS, $fields_string);

// Fire!
$result = htmlspecialchars_decode(curl_exec($ch));

// Close your connection
curl_close($ch);</pre>

And that&#8217;s it. The `$result` variable will contain the response from the request. Depending how this is provided it might be plain text, JSON or pretty much anything else imaginable (over HTTP). 

If it is a JSON string it can be converted to an object as follows: 

<pre>$decode = json_decode($result);</pre>

Where `$decode` is a PHP object.