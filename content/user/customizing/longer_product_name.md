---
title: Longer Product Name 
description: How do I increase the length of the product name field?
category: customizing 
weight: 10
---

The product name field can be lengthened by running these two commands in the `Tools > Install SQL Patches` page: 

```
ALTER TABLE products_description MODIFY COLUMN products_name varchar(191) NOT NULL default '';
ALTER TABLE orders_products MODIFY COLUMN products_name varchar(191) NOT NULL default '';
```

Note that the product name data is stored in two tables. The same is true of other fields in Zen Cart; when you expand a field, be sure to do all locations.  Other similar examples: 

- Company name is in the `address book` table and the `orders` table (and is stored three times in the orders table, since customer, shipping and billing can all be different). 
- Products Model is in the `products` and `orders_products` tables. 

