---
title: Blank Page (or partial blank page) troubleshooting
category: troubleshooting 
weight: 1
---
Blank pages can be caused by a number of things, and often occur just after installing, upgrading, or customizing your store. Any time you touch a PHP file, you must be sure to not introduce syntax problems, and you need to be sure that it uploaded correctly.  

## 1\. Did all your file-uploads work properly?

Sometimes FTP programs experience a timeout when uploading large quantities of files (such as when installing or upgrading your site), or fail to fully upload some files, or leave them as just 0-bytes in size.  
Some programs like SmartFTP and CuteFTP are well-known to be problematic in this area.  
For Windows PCs, you'll find [FileZilla](http://filezilla.sf.net) is a free, fast, and reliable FTP program (but don't save your passwords with it!).  
On Mac, Transmit or Forklift or CyberDuck are commonly acclaimed FTP tools.  

Best to re-upload and ensure that there are no errors, and that no files are left with 0 bytes.  

<font color="#a52a2a">**Failed uploads are the MOST COMMON CAUSE of all website problems.** </font>

## 2\. Have you created any syntax errors in your customizations and/or file edits?

A PHP syntax error will very often result in a blank screen, or a partially-blank screen.  
When this happens, there is often also an entry in the server's errorlog, which you can often view via your hosting control panel area. But, sometimes you can't view that log without requesting your hosting company to access it for you, for privacy reasons. So, alternatively you can use the debug logging built-in to Zen Cart:  

### a) Check for the actual error messages in the store's myDebug-xxxxxxx.log files:

The built-in debug logging will create files <font color="#0000FF">**in your website's /logs/ folder**</font>, named "<font color="#0000FF">**myDebug-xxxxxx.log**</font>" (or "myDebug-adm-xxxxxxx.log" if they are from the admin side).  
(To access these files, use your FTP program to connect to your webserver. Your hosting company can help you with how to do that.)  
(If there are no myDebug-xxxxxxxxxxx.log files in your /logs/ folder, then you might need to [make your /logs/ folder writable.](/user/installing/permissions).
Contact your hosting company's help desk if you need assistance with that.)  
You'll want to read the contents of these files to see what the actual PHP errors are.  
Then search this FAQ area for your error message and/or see the "Dealing with Error Messages" section, later in this article.  

NOTE: When errors start occurring, the number of log files in this folder can grow very quickly. You can purge them by using the Debug Log File Purge option from your Admin->Tools->Store Manager screen.  
You will of course want to review the contents of those files first so you can address the problems they're recording.  
If you don't purge them, it will eventually slow down your website's performance, and use up a large amount of disk space.  

NOTE: If you're running Zen Cart v1.3.8 or older, you REALLY need to UPGRADE ASAP! In the meantime, to enable the debug logging on older versions, use the [Debug Error-Logging Tool](http://www.zen-cart.com/downloads.php?do=file&id=606) from our downloads area.  

### b) Dealing with the Error Messages

Kinds of errors:  

*   The "fatal" messages are the more important ones to deal with.
*   "Notice" messages can be ignored in most cases.
*   "Warnings" should draw some attention, but are not fatal.

How to read the errors:  

*   Note that many error/warning messages will be a result of previous error/warning messages.  
    <font color="#FF0000">**Deal with them in the order they appear**,</font> and don't blame the later errors until the earlier ones are dealt with first.
*   One of the MOST COMMON errors you'll see is addressed here: [Warning: Headers Already Sent ...](/user/troubleshooting/warning_headers_already_sent).
*   Use the search option on this page to find answers to any other errors you find.

## 3\. Common customization errors

The most common customization errors include:  

*   adding or deleting apostrophes or quotations (ie: ' or " marks) inside define() statements, resulting in mismatched quotes
*   removing or adding punctuation to define() statements, thus breaking the correct syntax. A define() statement should look like this:


`define('CONSTANT_NAME', 'value here');`

*   missing semi-colons and periods, unbalanced parentheses, braces, brackets
*   uploading files to the wrong places. For more information about overrides, see the [Overrides Chart](http://www.zen-cart.com/index.php?main_page=product_contrib_info&cPath=40_54&products_id=298) and the [Overrides FAQs](http://tutorials.zen-cart.com/index.php?category=4)
*   When renaming files (for backup), be sure to NOT keep the extension ".php". For instance, rename header_php.php to header_php.old or header_php.php.20110701, BUT *NOT* header_php.old.php.

## 4\. Bad product data

(This refers to product pages mainly, not "all pages".)  
Sometimes when entering product data, if you copy+paste from another application (especially MS Word), weird "special" characters might get inserted, which can cause trouble in unexpected places. Make sure your product names and descriptions are clean.  

And for product-images, make sure you don't have spaces and hyphens in the product-image-filenames.  

* * *

**Other Information**  
If you are using Yahoo Hosting, you might want to enable their [script logs](http://help.yahoo.com/l/us/yahoo/smallbusiness/webhosting/php/php-05.html)  

* * *

### Advanced Developer Option. (THIS APPROACH IS *NOT* NEEDED FOR MOST SITUATIONS!!!!)

While **<font color="#ff0000">the built-in myDebug-xxxxxx.log method above is far more reliable and secure</font>** (since messages are never shown in your customers' browser), another way to help identify ***where*** an error is happening is to show the errors on your browser. The drawback to this is that your customers can also see the errors, and search engines might catch them too, which could be embarrassing, AND WILL CAUSE YOUR SITE TO FAIL PCI SECURITY SCANS.  
To attempt to show PHP debug errors on-screen, create and upload a new file, like this:  
Filename: **/includes/<u>local</u>/configure.php**  

```
<?php
  define('STRICT_ERROR_REPORTING', true);
?> 
```

Then try to access your site again. You may see many warning messages on the screen.  

Be sure to delete the `/includes/local/configure.php` file once you've identified the problem, lest you leave yourself with a security problem on your site.
