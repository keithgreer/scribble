---
id: 983
title: 'Magento Code: Check an import directory for new product CSVs and process using a Magmi profile'
date: 2017-06-07T13:55:31+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=983
permalink: /magento-check-an-import-directory-for-new-product-csvs-and-process-using-a-magmi-profile
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
image: /cms/wp-content/uploads/2016/02/magento-generic.png
categories:
  - Code
tags:
  - CSV
  - Import
  - Magento Code
  - Magmi
  - PHP
---
This script will first scan the var/import directory for all CSV files starting &#8220;import-&#8221; using the [`glob()`](/php-glob) function in PHP. It will return an array of any files which match the query in the directory including the file path from root.

The `$file_parts` will be used later when we need just the file name.

`$cmd` is the executable shell command we will be using to load Magmi, set the profile, mode and chosen file.

The `shell_exec()` function runs the command and will return any output to the `$output` variable, this can be expanded to check for a successful import. The script below will carry on regardless of import status.

Once the import is complete we take the CSV and copy it into an archive folder, just in case we want to reuse it. The original file is then deleted from the var/import folder using `unlink()`

This script can then either be run manually, or set-up as a scheduled task using Cron.

<pre>// Find all CSV files in import directory
$files = glob('/home/admin/public_html/var/import/import*.csv');

// For each of the files found 
foreach ($files as $file):

   // Explode for teh the file name in 6th position of the array
   $file_parts = explode("/",$file);

   // Set-up the command 
   $cmd = 'php /home/admin/public_html/magmi/cli/magmi.cli.php -profile=default -mode=create -CSV:filename="'.$file.'"';

   // Execute the comamnd 
   $output = shell_exec($cmd);

   // Copy the executed script into an archive folder
   if ( copy($file,'/home/admin/public_html/var/import/archive/'.$file_parts[6]) ):
      // Delete the original
      unlink($file);
   endif;

endforeach;</pre>