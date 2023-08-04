---
title: Blank Page troubleshooting
description: How do I fix a blank page or partial blank page? 
category: troubleshooting 
weight: 10
---

A blank page (or partial blank page) occurs when the PHP interpreter 
has a fatal error creating your page. 

The image on the left is a blank page.  The image on the right, which is missing the site footer, is also a blank page. 

Blank Page | Partial Blank Page 
----|----
![Blank Page](/images/blank_page_1.png) | ![Partial Blank Page](/images/blank_page_2.png)


Blank pages can be caused by a number of things, and often occur just after installing, upgrading, or customizing your store. Any time you touch a PHP file, you must be sure to not introduce syntax problems, and you need to be sure that it uploaded correctly.  

## 1\. Did all your file-uploads work properly?

Sometimes [FTP tools](/user/first_steps/useful_tools/#ftp-tools) experience a timeout when uploading large quantities of files (such as when installing or upgrading your site), or fail to fully upload some files, or leave them as just 0 bytes in size.  

Some programs like SmartFTP and CuteFTP are well-known to be problematic in this area.  See [FTP tools](/user/first_steps/useful_tools/#ftp-tools) for a list of alternatives. 

Best to re-upload and ensure that there are no errors, and that no files are left with 0 bytes.  

You can easily verify that you do not have any zero byte files in your 
installation by using the [Changed Files plugin](https://www.zen-cart.com/downloads.php?do=file&id=2193). 

<font color="#a52a2a">**Failed uploads are the MOST COMMON CAUSE of all website problems.** </font>

## 2\. Have you created any syntax errors in your customizations and/or file edits?

A PHP syntax error will very often result in a blank screen, or a partially-blank screen.  

When this happens, there is often also an entry in the server's errorlog, which you can often view via your hosting control panel area. But, sometimes you can't view that log without requesting your hosting company to access it for you, for privacy reasons. So, alternatively you can use the debug logging built-in to Zen Cart, which is described below. 

Other pages in this documentation show some common examples of [syntax errors](/user/upgrading/php_warnings/) and how to fix them.

## 3\. Are you running an older cart on a newer PHP? 

**Note:** Your hoster may have updated your PHP underneath you; be sure to 
[check your PHP version](/user/admin_pages/admin_version/) to be sure!

If your hoster updated your PHP version, be aware that if you're running an old version of Zen Cart, you could have problems - refer to the [PHP Version - Zen Cart version compatibility matrix](/user/first_steps/server_requirements/#php-version). 

## 4\. Have you recently made a code change? 

The most common customization errors include:  

*   adding or deleting apostrophes or quotations (ie: ' or " marks) inside `define()` statements, resulting in mismatched quotes
*   removing or adding punctuation to define() statements, thus breaking the correct syntax. A define() statement should look like this:

```
    define('CONSTANT_NAME', 'value here');
```

*   missing semi-colons and periods, unbalanced parentheses, braces, brackets
*   uploading files to the wrong places. For more information about overrides, see the [Overrides Chart](https://www.zen-cart.com/downloads.php?do=file&id=192)
and the [Overrides FAQs](/user/template/template_overrides/). 
*   When renaming files (for backup), be sure to NOT keep the extension ".php". For instance, rename header_php.php to header_php.old or header_php.php.20110701, **NOT** header_php.old.php.

## 5\. Do you have bad product data?

(This refers to product pages like `product_info` mainly, not all pages.)  
Sometimes when entering product data, if you copy+paste from another application (especially MS Word), weird "special" characters might get inserted, which can cause trouble in unexpected places. Make sure your product names and descriptions are clean.  

And for product-images, make sure you don't have spaces and hyphens in the product-image-filenames.  

## 6\. Checking file loading 

Turning on file loading debugging can help pinpoint some issues. 

If your admin is failing to load, try temporarily editing 
`admin/includes/application_bootstrap.php`, and change 

```
define('DEBUG_AUTOLOAD', false);
```

to 

```
define('DEBUG_AUTOLOAD', true);
```

Then re-load the admin page and look for failures in the output.  You might see something like 

```
[286] => processing class - /home/client/public_html/includes/classes/pulldown.php
[287] => loading class - /home/client/public_html/includes/classes/pulldown.php - FAILED
```

which tells you the file `includes/classes/pulldown.php` is bad or missing. 

The same test can be run on the storefront by editing `includes/application_top.php` and turning on `DEBUG_AUTOLOAD` there..

Be sure to restore these files once you are done testing. 


## Working with Debug Logs

### a) Looking at log files 

The built-in debug logging will create files 
in your website's /logs/ folder named 
`myDEBUG-xxxxxx.log`
(or `myDEBUG-adm-xxxxxx.log` if they are from the admin side).  

To access these files, use your [FTP program](/user/first_steps/useful_tools/#ftp-tools) to connect to your [hoster](/user/first_steps/hosting/#hosting-companies).

If there are no myDEBUG-xxxxxx.log files in your /logs/ folder, then you might need to [make your /logs/ folder writable](/user/installing/permissions/).

You'll want to read the contents of these files to see what the actual PHP errors are.  

Once you have a log, see [reading a myDEBUG log](/user/troubleshooting/debug_logs/). 

Then search this FAQ area for your error message and/or see the "Dealing with Error Messages" section, later in this article.  

**NOTE:** When errors start occurring, the number of log files in this folder can grow very quickly. You can purge them by using the Debug Log File Purge option from your Admin > Tools > Store Manager screen.  

You will of course want to review the contents of those files first so you can address the problems they're recording.  

If you don't purge them, it will eventually slow down your website's performance, and use up a large amount of disk space.  

**NOTE:** If you're running Zen Cart v1.3.8 or older, you REALLY need to UPGRADE ASAP! In the meantime, to enable the debug logging on older versions, use the [Debug Error-Logging Tool](https://www.zen-cart.com/downloads.php?do=file&id=606) from the Zen Cart plugins library.  

### b) Using Error Messages

Kinds of errors:  

*   The "fatal" messages are the more important ones to deal with.
*   "Notice" messages can be ignored in most cases.
*   "Warnings" should draw some attention, but are not fatal.

How to read the errors:  

*   Note that many error/warning messages will be a result of previous error/warning messages.  <font color="#FF0000">**Deal with them in the order they appear**,</font> and don't spend time on the later errors until the earlier ones are dealt with first.
*   One of the MOST COMMON errors you'll see is addressed here: [Warning: Headers Already Sent ...](/user/troubleshooting/warning_headers_already_sent/).
*   Use the search option on this page to find answers to any other errors you find.

### c) Missing Log Files 

If you're seeing a blank screen but have no log files in your /logs/ folder,
it could be that your configuration has changed the default logging behavior.  See [Missing Log files](/user/troubleshooting/missing_log_files/). 

### d) Common fixes 

The [Upgrading plugins to 1.5.8](/dev/plugins/upgrading_to_158) page shows some common issues and fixes.

* * *

### Advanced Developer Option. (THIS APPROACH IS *NOT* NEEDED FOR MOST SITUATIONS!!!!)

While **<font color="#ff0000">the built-in myDEBUG-xxxxxx.log method above is far more reliable and secure</font>** (since messages are never shown in your customers' browser), another way to help identify ***where*** an error is happening is to show the errors on your browser. The drawback to this is that your customers can also see the errors, and search engines might catch them too, which could be embarrassing, AND WILL CAUSE YOUR SITE TO FAIL PCI SECURITY SCANS.  

To attempt to show PHP debug errors on-screen, create and upload a new file, like this:  
Filename: **/includes/<u>local</u>/configure.php**  

```
<?php
  define('STRICT_ERROR_REPORTING', true);
```

(The missing `?>` is intentional.)

Then try to access your site again. You may see many warning messages on the screen.  

Be sure to delete the `/includes/local/configure.php` file once you've identified the problem, lest you leave yourself with a security problem on your site.
