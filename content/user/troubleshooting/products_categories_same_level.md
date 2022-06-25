---
title: Products and Categories at the Same Level 
description: Restrictions on category contents 
category: troubleshooting
weight: 10
---

A basic rule of product structure in Zen Cart is: Products must be placed inside categories; products and categories cannot coexist at the same level.

Nevertheless, sometimes this can happen: direct database updates, bugs in plugins, and other situations can lead to such a scenario. 

It's easy to see when this has happened; go into Admin > Catalog > Categories/Products, and look at your categories.  If you see the Action buttons out of alignment, you'll know your category has both categories and products.  You will also see the count at the bottom left hand side of the page show both products and categories.

![Products and Categories same level](/images/prod_cat_same_level.png)

To fix this situation, use the purple "M" (move) button as needed.  You may have to put a product in a category temporarily - as you can see, there is currently no "New Category" button on this page, because there's a product in this category.  Moving the product out will fix this issue. 

![Only Categories at a level](/images/prod_cat_same_level2.png)

If you have this problem in a number of places in your database, you might want to consider using the [Audit Plugin](https://www.zen-cart.com/downloads.php?do=file&id=2261) to track them all down and get them fixed. 


