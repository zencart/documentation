---
title: Creating or Modifying a table 
description: Modifying the database schema 
category: code
weight: 10
---

## Creating a New Table 

Creating a new table is done with the SQL `CREATE TABLE` command. You may provide a .sql file that does this operation with instructions to run the file in Admin > Tools > Install SQL Patches, or you may embed the CREATE TABLE operation in a file that is run automatically in the admin (for example, `admin/includes/functions/extra_functions/your-feature.php`). 

When you create a new table, be sure to create a defined constant for the table name on both the storefront and admin side.  Example: 

```
<?php
define('TABLE_PRODUCTS_XSELL', DB_PREFIX . 'products_xsell');
```

This would go in `includes/extra_datafiles/xsell_definitions.php` and `admin/includes/extra_datafiles/xsell_definitions.php`. 

## Modifying a Table 

Changing a table's structure - adding or removing fields, modifying default values and so forth - is done with the SQL `ALTER TABLE` command.  Again, you may provide a .sql file or automate this action. 


## Related Articles 
- [Adding a field to the products table](/dev/code/add_field_products/). 
