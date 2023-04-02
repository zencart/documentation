---
title: Date standardization 
description: Getting custom date fields set correctly 
category: Upgrading
weight: 10
---

**Note:** This guidance is only required if you have modified the structure
of your database to add custom `datetime` or `date` fields.  

#### Handling custom datetime/date fields in your database 
Zen Cart uses a specific string (rather than NULL) for `datetime` and `date` fields to indicate that a value has not been set. 

In older versions of Zen Cart, the string was `0000-00-00`. However, since then, MySQL has updated their definition of allowable date formats to exclude this string.  

Since Zen Cart 1.5.6, the upgrade process has included steps necessary to fix these older style dates as follows 
- update all rows in the table to change any `date` columns with the value `0000-00-00` to `0001-01-01`, and set the field's default value to `0001-01-01`. 
- update all rows in the table to change any `datetime` columns with the value `0000-00-00 00:00:00` to `0001-01-01 00:00:00`, and set the field's default value to `0001-01-01 00:00:00`. 

(In the case of `datetime` values, the appended value for time remains 00:00:00; it has not changed.) 

However, the upgrade process can only do this for built-in fields.  If you have customized your database to include additional fields (perhaps via a plugin, or perhaps with your own custom code), you will need to make the same changes to your own database.  Failure to do so can mean an incomplete upgrade that will have to be fixed by hand by re-applying the failed SQL statements. 

The debug log which is produced when a bad date is present will look like this: 

```
--> PHP Fatal error: 1292:Incorrect datetime value: '0000-00-00 00:00:00' for column 'customers_dob' at row 3048 :: ALTER TABLE zen_customers ADD tax_exempt tinyint(1) default 0; ==> (as called by) /Users/scott/Sites/store/admin/sqlpatch.php on line 291 <== in /Users/scott/Sites/store/includes/classes/db/mysql/query_factory.php on line 170.
```

Examples of plugins which add a 'bad' datetime or date field are: 

- [Order Delivery Date](https://www.zen-cart.com/downloads.php?do=file&id=683).  It adds a `datetime` field called `order_delivery_date` to the `orders` table. (Note: Some earlier versions of the plugin created this field as a `date`.)
- [Ceon Back In Stock Notifications](https://www.zen-cart.com/downloads.php?do=file&id=773).  It creates a `datetime` field called `date_subscribed` in a new table called `back_in_stock_notification_subscriptions`. 
- [Flexible Footer Menu Columns for 1.5.x](https://www.zen-cart.com/downloads.php?do=file&id=1726). It creates a field named `date_added` in the `flexible_footer_menu` table.

Example fix: 

To get the custom `datetime` field `order_delivery_date` into the new format, use following command in phpMyAdmin or in [Install SQL Patches](/user/admin_pages/tools/install_sql_patches/): 

````
```
UPDATE orders SET order_delivery_date = '0001-01-01 00:00:00' WHERE order_delivery_date IS NOT NULL AND CAST(order_delivery_date AS CHAR(19)) = '0000-00-00 00:00:00';
```
````

Then update the default value using 

```
ALTER TABLE orders MODIFY COLUMN order_delivery_date datetime NOT NULL default '0001-01-01 00:00:00';
```

To fix a custom field which is a `date` (instead of a `datetime`), the process is similar: 

```
UPDATE thetablename SET thefieldname = '0001-01-01' WHERE CAST(thefieldname AS CHAR(10)) = '0000-00-00';
```

Then update the default value of the field:

```
ALTER TABLE thetablename MODIFY COLUMN thefieldname date NOT NULL default '0001-01-01';
```

**Notes**: 

1. If you run any commands via phpMyAdmin and your site uses a `DB_PREFIX` (e.g. `zen_`), you will need to add that prefix to any database table name.  For the example above, you'll replace `orders` with `zen_orders`.
2. The PHP code that uses that custom field might be checking for the field's value to be '0000-00-00 00:00:00' (for a datetime field) or '0000-00-00' (for a date field).  So don't just fix your database - be sure to inspect the associated PHP code and make any changes required there too.


For reference, the script that does the date updating is stored in `zc_install/sql/install/zero_dates_cleanup.sql`. 

