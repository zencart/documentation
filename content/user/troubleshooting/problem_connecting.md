---
title: 'There seems to be a problem connecting to our database'
description:  What do I do when this message is shown? 
category: troubleshooting
weight: 10
---

If your database credentials have been altered incorrectly, you might receive an unexpected screen when visiting your store:

```
Sorry!
There seems to be a problem connecting to our database. Please give us a few minutes to remedy the problem. Thank you.
```

Common causes:

- You've changed your database name or database username on your webserver
- You've deleted the tables from the database on your server
- You've changed the `DB_PREFIX` setting in your [configure.php files](/user/miscellaneous/configure/) to a value that doesn't match the tables in your database
- You've edited your `/includes/configure.php` file and incorrectly altered the defined values for the various `DB_XXXXXX` settings contained therein. You should first go and fix those. Then make sure you've also got the correct values in the /your-renamed-admin-folder/includes/configure.php as well.

The error is specifically displayed when the `DB_XXXXXX` values (which mainly denote your database login credentials for MySQL) are used but return a security login error when trying to connect to the database.

If you don't know the correct database name, MySQL username and MySQL password, and database host name (servername),  then you need to talk to your hosting company's tech support staff for assistance.

**NOTE:** THIS ERROR MEANS THERE IS A PROBLEM ON *YOUR* SERVER. THE PROBLEM IS NOT WITH zen-cart.com AND ONLY YOU CAN FIX THE ERROR!

