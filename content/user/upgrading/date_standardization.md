---
title: Date standardization 
description: Getting custom date fields set correctly 
category: Upgrading
weight: 10
---

**Note:** This guidance is only required if you have modified the structure
of your database to add custom date fields.  

#### Handling custom date fields in your database 
Zen Cart uses a specific string (rather than NULL) for date fields to indicate that the date has not been set. 

In older versions of Zen Cart, the string was `0000-00-00`.  However, since then, mySQL has updated their definition of allowable date formats to exclude this string.  

Since Zen Cart 1.5.6, the upgrade process has included steps necessary to convert these older style dates (`0000-00-00`) to a newer value (`0001-01-01`), which is acceptable to mySQL. 

However, the upgrade process can only do this for built-in fields.  If you have customized your database to include additional fields (perhaps via a plugin, or perhaps with your own custom code), you will need to make the same changes to your own database. 

An example of a plugin which adds a date field is [Order Delivery Date](https://www.zen-cart.com/downloads.php?do=file&id=683).  It adds a field called `order_delivery_date` to the `orders` table. 

To get the custom `datetime` field `order_delivery_date` into the new format, use following command in phpMyAdmin or in [Install SQL Patches](/user/admin_pages/tools/install_sql_patches/): 

```
UPDATE orders SET order_delivery_date = '0001-01-01 00:00:00' WHERE CAST(order_delivery_date AS CHAR(19)) = '0000-00-00 00:00:00';
```

or if the field were just a `date` field then:
```
UPDATE thetablename SET thefieldname = '0001-01-01' WHERE CAST(thefieldname AS CHAR(10)) = '0000-00-00';
```

**Note**: If you run that command via phpMyAdmin and your site uses a `DB_PREFIX` (e.g. `zen_`), you will need to add that prefix to any database table name.  For the example above, you'll replace `orders` with `zen_orders`.



For reference, the script that does the date updating is stored in `zc_install/sql/install/zero_dates_cleanup.sql`.

