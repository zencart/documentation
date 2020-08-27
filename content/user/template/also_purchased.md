---
title: How do I enable "Customers Also Purchased" display? 
description: Showing what other customers purchased 
category: template
weight: 10
---

"Also Purchased" information may be shown on the [product info](/user/storefront_pages/product_info/) page.  This means customers can see which other products were purchased by customers viewing the product they are viewing.

To enable also purchased products display on the product info page, do the following: 

1. Set: [Admin > Configuration > Product Info > Also Purchased Products Columns per Row](/user/admin_pages/configuration/configuration_productinfo/#also_purchased_products_columns_per_row). 

2. Set: [Admin > Configuration > Minimum Values > Also Purchased Products](/user/admin_pages/configuration/configuration_minimumvalues/#also_purchased_products) to a value greater than 0.  If you always want to display also purchased products, use the value "1".  

A value larger than 1 (say "3") means "Display also purchased products only if there are three or more."  So if you set this value to 3, but there is only one also purchased product, no products will be shown.  

3. Set: [Admin > Configuration > Maximum Values > Also Purchased Products](/user/admin_pages/configuration/configuration_maximumvalues/#also_purchased_products) to a value greater than 1.

![Also Purchased Products](/images/also_purchased.png)



