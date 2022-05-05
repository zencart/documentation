---
title: How do I set up a default tax class for new products? 
description: Save time by pre-setting a tax class for product creation 
category: taxes
aliases: 
    - /user/localization/default_tax_class
    - /user/locations/default_tax_class
weight: 10
---

**Question:** Is there a way I can get the system to select a certain Tax class automatically when I'm adding a product? 

**Answer:** Yes - here's how: 

1. Find out the tax class ID number in [Admin > Locations/Taxes > Tax Classes](/user/admin_pages/locations/tax_classes/).  (It's the number on the left hand side.) 

2. Go to [Admin > Catalog > Product Types > Layout Settings](/user/admin_pages/catalog/product_types_edit_layout/)
for the product type you're using (probably `Product - General`)

Choose 
*Product Price Tax Class Default - When adding new products?*
and enter the tax class ID number you obtained in step 1 above.

Next time you add a product, the tax class is pre-selected.

If you want to do an audit of your database to see if any products are mis-coded, you can use a query like this: 

```
SELECT p.products_id, pd.products_name FROM products p, products_description pd WHERE p.products_id = pd.products_id AND products_tax_class_id != 1;
```

(This assumes that "Taxable Goods" is Tax Class id "1".)

