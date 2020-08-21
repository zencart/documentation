---
title: Troubleshooting errors after upgrading PHP versions 
description: Updating PHP causes new Debug Logs in Zen Cart 
category: troubleshooting
weight: 10
---

**Note:** On a [shared hosting](/user/first_steps/hosting/#hosting-companies) account, your hoster can just update PHP at any time - just because you didn't change anything doesn't mean it didn't change!  Check the [Admin Version link](/user/admin_pages/admin_version/) to verify your current version of PHP. 

PHP is a dynamic language which is continually being updated.  And part of 
the update process is sunsetting features, functions, syntax and other language elements: 

- the language designers decide to change how something works
- then the new way is introduced, and the old way is deprecated, 
- then the old way is eliminated entirely. 

The PHP.net website shows you the PHP lifecycle and [which PHP versions are current](https://www.php.net/supported-versions.php). 

The symptom you will see when this is an issue for you is that things 
that used to work (even yesterday) suddenly do not.  What might have 
happened in this case is that your hoster just changed your PHP version
without warning.  Alternatively, perhaps you upgraded your version of 
Zen Cart, but wound up using some old files.  

Each version of Zen Cart (and each plugin) 
was developed for the version of PHP that was
prevalent at the time, and may not be compatible with newer PHP versions.
See [mapping of Zen Cart versions to PHP versions](/user/first_steps/server_requirements/#php-version) more information.

Let's look at a specific example of how this can happen.  These examples will
appear dated in a few years,  but the principles remain the same - a 
language change was made that requires a change to your files. 

Suppose you are using Zen Cart 1.5.4 with PHP 5.6, and it's working fine.  Then you upgrade to Zen Cart 1.5.6 and move to PHP 7.1. 

At checkout time, you get a fatal error: 

```
PHP Parse error: syntax error, unexpected '[', expecting ',' or ';' in .../includes/modules/payment/paypalwpp.php on line 1148.
```

That's because in Zen Cart 1.5.4, this line of code (`paypalwpp.php`, line 1148)

```
global $$order_totals[$i]['code'];
```

was perfectly fine in PHP 5.6, but in PHP 7.1 needs to be changed to 

```
global ${$order_totals[$i]['code']};
```

**and if you don't change it, you'll get a blank screen**.

Another example would be a log like this: 

```
--> PHP Fatal error: Uncaught Error: Cannot use string offset as an array in ... /includes/modules/responsive_sheffield_blue/product_listing.php:260

```

Root cause: in older versions of PHP, it was acceptable to initialize an array as 

```
$list_box_contents = ''; 
```

but newer versions require

```
$list_box_contents = array();
```


To understand the log files that are created when issues like this
occur, see [debug logs](/user/troubleshooting/debug_logs/).


