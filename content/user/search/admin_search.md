---
title: Admin search
description: How you can search for products in the admin panel 
category: search 
weight: 10
---

The search in admin is shown as a field on the upper right hand side of the page Admin > Catalog > Categories/Products. 

![Admin Search](/images/admin_search.png)

The contents of the `search` field is used to search the following fields: 

Table | Fields 
------|-------
`categories_description` | `categories_id`, `categories_name`
`products_description` | `products_name`, `products_description`
`products`| `products_id`, `products_model`

You can see [the database schema](/dev/schema/) if you wish to learn more about how the database is structured. 

To add a field to the admin search (such as `products_mpn`, for example), use the notifier `NOTIFY_BUILD_KEYWORD_SEARCH` or modify `admin/category_product_listing.php` and change the first argument to `zen_build_keyword_where_clause`.   Note that `products_mpn` is added to the admin search in Zen Cart 2.1.0. 
