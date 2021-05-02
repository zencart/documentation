---
title: PHP Memory Limit 
description: Checking and updating your PHP memory\_limit
category: running 
weight: 10 
---

The PHP Memory Limit is the amount of memory a script is allowed to allocate, per the [PHP Documentation on this setting](https://www.php.net/manual/en/ini.core.php#ini.memory-limit).  Suggestions on setting this value are provided in [PHP memory limit and Zen Cart](/user/first_steps/server_requirements/#php-memory-recommendations).

In some environments, changing your PHP version can reset your memory limit setting.  Go to the [version page](/user/admin_pages/tools/server_info/) after updating PHP to verify the setting of your PHP Memory Limit.

The process of updating your PHP memory is server-specific:

- Some hosts running cPanel provide PHP Selector, which has a page for PHP Options 
- Some hosts running cPanel provide MultiPHP INI Editor 
- Some hosts use `php.ini` files 

Your hoster likely provides a knowledge base with instructions.  Contact your hoster if you are unsure how to proceed. 


