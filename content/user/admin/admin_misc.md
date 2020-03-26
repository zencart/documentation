---
title: Miscellaneous questions about the Admin
description: Miscellaneous questions about Zen Cart Admin
category: admin
weight: 5
---

{{< misc >}} 

---
### What determines if a product is New?

There are settings in [Admin->Configuration->Maximum Values](/user/admin_pages/configuration/configuration_maximumvalues/) to determine what "New Product" means: 

```
New Product Listing - Limited to ...
Limit the New Product Listing to
0= All Products
1= Current Month
7= 7 Days
14= 14 Days
30= 30 Days
60= 60 Days
90= 90 Days
120= 120 Days
```


ALTERNATIVE:
If, however, you wish to hand-pick which items show up, then turn OFF the *New Products* box, and use *Featured Products* instead.  See [Admin->Catalog->Featured Products](/user/admin_pages/catalog/featured/) to pick the products. 


---
### How do I get my store home page to open to a certain category?

Open the [Admin->Configuration->Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/). 

Find "Main Page - Opens with Category"

Type in the category you wish to open to.

```
example: 25  or 3_10 or 24_41_79
```

Then press *Save*. 

---
### How do I enable the "Customers Also Purchased" display?

1. You need to have purchases in your store first ... where customers bought "this" product along with "another" product.

2. Set: [Admin->Configuration->Product Info->Also Purchased Products Columns per Row](/user/admin_pages/configuration/configuration_productinfo/#also_purchased_products_columns_per_row). 

3. Set: [Admin->Configuration->Maximum Values->Also Purchased Products](/user/admin_pages/configuration/configuration_maximumvalues/#also_purchased_products).

--- 
### Is there a way that I can check on what users with Admin access to my site are doing?

There isn't currently a Zen Cart page to do this, but each time an Admin page is called, the access date, admin ID, page accessed, page parameters and IP address are logged in the admin_activity_log table. The contents of this table can be viewed via database management tools such as phpMyAdmin.

--- 
### How do I add or delete categories? 
See [how do I add a new category?](/user/categories/add_delete/#how-do-i-add-a-new-category) and 
[how do I delete a category?](/user/categories/add_delete/#how-do-i-delete-a-category)

--- 
### How do I add or delete products? 
See [how do I add a new product?](/user/products/add_delete/#how-do-i-add-a-new-category) and 
[how do I delete a product?](/user/products/add_delete/#how-do-i-delete-a-category)

--- 
### How do I use another currency instead of US Dollars?
See [how do I use another currency?](/user/localization/my_currency) 

---
<!-- please keep this at the end --> 
{{< faq_questions >}}
