---
title: ERROR 0071 - There appears to be a problem with the database
description: What do to when it says "Maintenance is required."
category: troubleshooting 
weight: 10
---

This error generally means that one or more system tables cannot be found in the database.

Common causes:

- Database connection problem, such as when the MySQL database service is down or restarting.
- Database tables are corrupt and needing repair. (Repair them using phpMyAdmin).
- Empty database. This can occur if you've provided valid DB credentials in your [configure.php files](/user/miscellaneous/configure/) and the database itself exists but contains no tables. In this case you need to run `zc_install` to properly setup the database contents.
- Tables missing.  Did you recently "upgrade" but haven't yet run `zc_install` to create the proper tables?
- Wrong table-prefix setting. This symptom most commonly occurs when moving your site to another server and not properly preserving the `DB_PREFIX` setting from the old site's configure.php into the new site's configure.php, thus the tablenames cannot be located because they don't match up properly. Or you need to import the correct matching database data, since what you've got in the database presently isn't suitable for your current `DB_PREFIX` configuration.

(To manually figure out the correct prefix to use, look at the database using phpMyAdmin and see what common 2-4 letter prefix starts all the tablenames. Then set that value into the `DB_PREFIX` definition in your `configure.php` file.)

