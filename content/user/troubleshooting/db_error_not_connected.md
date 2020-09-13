---
title: 0 DB_ERROR_NOT_CONNECTED
description: What do I do with this message? 
category: troubleshooting
weight: 10
---

`DB_ERROR_NOT_CONNECTED` occurs when something is wrong with your database.

Possible Causes: 

1. Your `/includes/configure.php` and `/admin/includes/configure.php` files contain settings for the database (`DB_SERVER`
`DB_SERVER_USERNAME`, `DB_SERVER_PASSWORD`, `DB_DATABASE`, `DB_PREFIX`), which are used to log in to the database.

    The `0 DB_ERROR_NOT_CONNECTED` error occurs when those database settings no longer match the actual details for the MySQL server, the MySQL database, or the MySQL user+password, or if the database server is broken for some reason.

    Or, if you recently changed your MySQL user/database/password and didn't put those same changes into your `configure.php` files, you'll need to update your `configure.php` files to match what's required by your MySQL database server. 

2. Some frequently updated tables (such as `sessions` or `whos_online` 
can become corrupt, and cause this problem.  Run a "repair" on the database. Most hosts have a Database Repair option listed beside the database names in the webhosting control panel. Ask your host if you need help finding this.

3. Talk to your hosting company to determine whether they are doing some sort of maintenance on the database.  Tell them that your website cannot connect to your MySQL database, and ask them for some assistance in getting that working again.

