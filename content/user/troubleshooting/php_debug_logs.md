---
title: Understanding problems that occur after upgrading PHP versions 
description: Updating PHP causes new Debug Logs 
category: troubleshooting
weight: 10
---

This page explains *why* PHP warnings can suddenly start occurring.  An explanation of *how to fix them* is provided in [PHP Warnings and Deprecated messages after upgrading](/user/upgrading/php_warnings/).

PHP debug logs can suddenly start appearing in the following cases: 

- using an older plugin which has not been updated on a newer version of PHP.
- updating the PHP version on your website
- upgrading your site and changing PHP versions but forgetting a few files

**Note:** On a [shared hosting](/user/first_steps/hosting/#hosting-companies) account, your hoster can just update PHP at any time - just because **you** didn't change anything doesn't mean it didn't change!  

Check the [Admin Version link](/user/admin_pages/admin_version/) to verify your current version of PHP. 

PHP is a dynamic language which is continually being updated.  And part of the update process is sunsetting features, functions, syntax and other language elements: 

- the language designers decide to improve/change how something works
- then the new way is introduced, and the old way is deprecated for awhile, 
- then the old way is eliminated entirely. 

The `php.net` website shows you the PHP lifecycle and [which PHP versions are current](https://www.php.net/supported-versions.php). 

The symptom you will see when this is an issue for you is that things that used to work (even yesterday) suddenly do not. 
What might have happened in this case is that your hoster just upgraded your PHP version without warning.  
Alternatively, perhaps you upgraded your version of Zen Cart, but wound up using some old files designed for an older PHP version.

Each version of Zen Cart (and each plugin) was developed for the version of PHP that was prevalent at the time, and may not be compatible with newer PHP versions.
See [mapping of Zen Cart versions to PHP versions](/user/first_steps/server_requirements/#php-version) for more information about which PHP version is compatible with your Zen Cart version. 



