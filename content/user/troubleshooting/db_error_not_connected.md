---
title: 0 DB_ERROR_NOT_CONNECTED
description: What do I do with this message? 
category: troubleshooting
weight: 10
---

`DB_ERROR_NOT_CONNECTED` occurs when Zen Cart has trouble connecting to your database.

Possible Causes: 

1. Your `/includes/configure.php` and `/admin/includes/configure.php` files specify a [prefix](/user/first_steps/database/#what-are-prefixes) for your database tables (`DB_PREFIX`) which does not match what was used when creating the tables.  Not matching the prefix value (or specifying one when it is not needed) is a very common mistake for older installations being upgraded.  View your database in phpMyAdmin and see if a prefix is used.  The first Zen Cart table should be called (something like) `address_book`. 

   If it is called `address_book`, then your `DB_PREFIX` value should be `''`.

   `define('DB_PREFIX', '');`

   If it is called `zen_address_book`, then your `DB_PREFIX` value should be `'zen_'`. 

   `define('DB_PREFIX', 'zen_');`

   If it is called `zcaddress_book`, then your `DB_PREFIX` value should be `'zc'`. 

   `define('DB_PREFIX', 'zc');`

2. Your `/includes/configure.php` and `/admin/includes/configure.php` files contain settings for the database (`DB_SERVER`
`DB_SERVER_USERNAME`, `DB_SERVER_PASSWORD`, `DB_DATABASE`), which are used to log in to the database.

    The `0 DB_ERROR_NOT_CONNECTED` error can occur when those database settings no longer match the actual details for the MySQL server, the MySQL database, or the MySQL username+password, or if the database server is broken for some reason.

    For example, if you recently changed your MySQL username/database/password and didn't put those same changes into your `configure.php` files, you'll need to update those files to match what's required by your MySQL database server. 

3. Some frequently updated tables (such as `sessions` or `whos_online` 
can become corrupt, and cause this problem.  Run a "repair" on the database. Most hosts have a Database Repair option listed beside the database names in the webhosting control panel. Ask your host if you need help finding this.

4. Talk to your hosting company to determine whether they are doing some sort of maintenance on the database.  Tell them that your website cannot connect to your MySQL database, and ask them for some assistance in getting that working again.

