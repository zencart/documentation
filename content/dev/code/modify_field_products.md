---
title: Modifying a field in the products table 
description: How to modify a field in the products table 
category: code
weight: 10
---

To modify a field to make it longer, use the SQL `ALTER TABLE` command.  Just be sure you also modify the other copies of the field which may exist in other tables, such as the `orders_products` table.   

As an example, here's how to modify the `products_model` field in the products table: 

Make a backup of your database. Then in phpMyAdmin:

```
ALTER TABLE orders_products MODIFY COLUMN products_model varchar(40) default NULL;

ALTER TABLE products MODIFY COLUMN products_model varchar(40) default NULL;
```

(The value 40 could be whatever you want but it should be the same in both.)

If your database uses a prefix, you must use it on those two table names (e.g. `ALTER TABLE zen_orders_products`, `ALTER TABLE zen_products`).


### Related 
- [How to add a field to the products table](/dev/code/add_field_products)
