---
title: Server/Version Info 
description: Zen Cart Server/Version Info  Admin Page 
category: admin_pages
weight: 60
---

This page allows you to view information about the server 
on which you are running Zen Cart. 

The information at the top of the page gives you a quick snapshot of the most 
critical values: 

- PHP Version: Version of PHP you are using 
- Database Engine: Version of MySQL you are using 
- PHP Memory Limit: [The amount of memory a script is allowed to allocate](https://www.php.net/manual/en/ini.core.php#ini.memory-limit)
- Database: (Since Zen Cart 1.5.6) the name of the database from your `admin/includes/configure.php` file 

Below this is the history of your database.

Below this area is the output of [`phpinfo()`](https://www.php.net/manual/en/function.phpinfo.php). 

Be sure the version of PHP you are running is a 
[supported version](https://www.php.net/supported-versions.php). 
Running an older unsupported version leaves you vulnerable to attack 
by bad guys.  Stay up to date! 


