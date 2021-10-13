---
title: What is STRICT mode for my database? 
description: MySQL STRICT mode and its impact 
category: troubleshooting
weight: 10
---

Newer versions of MySQL enforce a greater number of rules relating to interacting with the database.  This can cause issues for code which was created prior to these rules being enforced. 

This issue *generally* won't happen to modern unaltered vanilla Zen Cart stores; this happens most often when you modify the database schema but don't upgrade the code to go with it. 

## Example of MySQL Strict Mode Error

Here's an example: 

You add a field called `gift_requested` to the `orders` table to represent something the customer requested at checkout.  The field is `NOT NULL` but with no default.

In prior versions of MySQL, this worked.  

Newer versions will fail saying:
```
ERROR 1364 (HY000): Field 'gift_requested' doesn't have a default value
``` 

## Temporary Fix To Disable MySQL Strict Mode

There's a (temporary) workaround for this issue.  In your [configure.php files](/user/miscellaneous/configure/), you can turn off the use of MySQL strict mode, until you can upgrade your Zen Cart code and your database structure.

Use or add the define, toward the bottom of the file:
```
  define('DB_MYSQL_MODE', 'NO_ENGINE_SUBSTITUTION');
```

(eg: according to the [MySQL docs](https://dev.mysql.com/doc/refman/8.0/en/sql-mode.html), setting it to a mode like NO_ENGINE_SUBSTITUTION skips strict mode because there are other mode names that handle strict-related things. Again, this should only be a temporary measure until you update your database and query code.)

The define for `DB_MYSQL_MODE` will work in Zen Cart 1.5.5 and above.  
In Zen Cart versions older than 1.5.5, you would need to do more extensive modification to interoperate with newer versions of MySQL.  Hopefully you are not doing this!  You should really [upgrade Zen Cart](/user/upgrading/) instead!

## Properly Fixing
Also note that turning off STRICT mode **is only a temporary workaround**. The correct solution is to update your code.  

In the case of the example above, there are two options: 

a) **Modify the database**: correct the syntax to match your PHP code's expectations:
`ALTER TABLE orders MODIFY COLUMN gift_requested char(1) NOT NULL default 'N'; ` 

b) **Modify your code**: when you perform an `INSERT` into the orders table, include the field `gift_requested` to the list of fields being updated (along with its value) so that it will have a value. 

--- 

## Notes

**NOTE:** Setting `DB_MYSQL_MODE` to `STRICT` is not the same as [strict error reporting](/user/troubleshooting/strict_error_reporting/). They are unrelated topics.

