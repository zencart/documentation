---
title: PHP Version and Configuration 
description: Changing PHP version or PHP Settings 
category: upgrading 
weight: 10
---

Before changing PHP versions, check [which PHP versions are available](/user/upgrading/check_php_version).  If the one you want isn't available, contact your hoster. 

The process of changing your PHP version is server-specific:
- Some hosts running cPanel provide MultiPHP Manager tool
- Some hosts running cPanel provide PHP Selector 
- Some hosts use a `php.ini` file

The process of changing PHP settings is also server-specific:
- Some hosts running cPanel provide MultiPHP INI Editor 
- Some hosts running cPanel provide PHP Selector which has a page for configuring PHP settings 
- Some hosts use a `php.ini` file
 
Your hoster likely provides a knowledge base with instructions.  Contact your hoster if you are unsure how to proceed. 

If you want to run multiple versions of PHP on your server (for example, to keep a live site going with an older version and test an upgrade with a newer version), see [Multiple PHP Versions](/user/upgrading/multiple_php_versions/).

Once you are done changing PHP version or a PHP setting, use the 
[Version](/user/admin_pages/admin_version/) link on the top right navigation menu to confirm that the change you made is recognized by Zen Cart. 

## Changing PHP Versions with MultiPHP Manager

MultiPHP Manager provides a dropdown list of PHP versions; simply select the one that is right for your cart, select the domain from the list below it, and press Apply. 

![MultiPHP Manager](/images/multiphp.png)

## Changing PHP Versions with PHP Selector 

PHP Selector (Select PHP Version) provides a dropdown list of PHP versions; simply select the one that is right for your cart, select the domain from the list below it, and press Apply. 

![PHP Selector](/images/phpselector.png)

## Changing PHP Configuration with MultiPHP INI Editor 
The Basic Mode of MultiPHP INI Editor allows you to use a form to set some key variables, such as `memory_limit`.   For other variables, it provides a file editor for you to use a `php.ini` file.  

![MultiPHP Manager](/images/multiphpini.png)

## Changing PHP Configuration with PHP Selector 

The PHP Options screen (launched from the Options tab) at the top of PHP Selector allows you to set common configuration variables for PHP. 

![PHP Selector](/images/phpselector_options.png)

The PHP Extensions screen (launched from the Extensions tab) at the top of PHP Selector allows you to include PHP libraries. 

![PHP Selector](/images/phpselector_extensions.png)

