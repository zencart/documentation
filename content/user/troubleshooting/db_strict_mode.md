---
title: What is STRICT mode for my database? 
description: Zen Cart MySQL database STRICT mode
category: troubleshooting
weight: 10
---

Newer versions of MySQL enforce a greater number of rules relating to 
interacting with the database.  This can cause issues for code which 
was created prior to these rules being enforced. 

This issue *generally* won't happen to modern unaltered vanilla Zen Carts; this happens most often 
when you modify the database schema but don't upgrade the code to go 
with it. 

Here's an example: 

- you add a field called `gift_requested` to the `orders` table to represent something the customer
requested at checkout.  The field is `NOT NULL` but with no default.

- In prior versions of MySQL, this worked.  Newer versions will fail saying
```
ERROR 1364 (HY000): Field 'gift_requested' doesn't have a default value
``` 
Happily, there's a workaround for this issue.  In your 
[configure.php files](/user/miscellaneous/configure/), you can turn off the enforcement of strict rules. 

Use the define 
```
  define('DB_MYSQL_MODE', 'NO_ENGINE_SUBSTITUTION');
```

This can be considered the opposite of 

```
define('DB_MYSQL_MODE', 'STRICT');
```

The define `DB_MYSQL_MODE` will work in Zen Cart 1.5.5 and above.  
In Zen Cart versions older than 1.5.5, you would need to do
more extensive modification to interoperate with newer versions
of MySQL.  Hopefully you are not doing this!  
You should really [upgrade Zen Cart](/user/upgrading/) instead!

Also note that turning on STRICT mode should be a temporary work around.
The correct solution for the longer term is to update your code.  In
this case, there are two options: 

a) Modify the database: `ALTER TABLE orders MODIFY COLUMN gift_requested char(1) NOT NULL default 'N'; ` 

b) Modify your code: when you perform an `INSERT` into the orders table, add 
the field `gift_requested` to the list of fields being updated so that it will have a value. 

--- 

**NOTE:** Setting `DB_MYSQL_MODE` to `STRICT` is not the same as 
[strict error reporting](/user/troubleshooting/strict_error_reporting). 

