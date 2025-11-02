---
title: Missing Products Description records 
description: Handling product table records which lack matching product_description records 
category: database
weight: 10
---

Each record in the product table records should have a matching record in the `product_description` table.  If the `products_description` table record is missing, many kinds of operations (attempting to view the product in the storefront, attempting to find the product in the admin, etc.) will not work. 

To fix missing `product_description` records, see this forum thread: 

https://www.zen-cart.com/showthread.php/230635-Logs-created-by-products-with-missing-description-records?p=1409398
