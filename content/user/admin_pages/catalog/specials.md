---
title: Specials 
category: admin_pages
weight: 120
---

This page allows you to view, edit or delete special pricing. 

Specials are price reductions on *individual* products, versus [Sales](/user/admin_pages/catalog/salemaker/), which are price reductions on one more more *categories* of products.  See [Salemaker vs Specials](/user/miscellaneous/salemaker_vs_specials/).

Opening up the specials page shows a list of the specials that have been created.

![Specials](/images/specials.png)

Since 1.5.7, Specials can be added in one of two ways: 

- By selection (from a list of all products)

- By Product ID (from a text field where the product ID is entered)

The latter technique was added because a list of all products is unwieldy for stores with a large number of SKUs. 

When selection from a list is used, a new window is opened allowing the product to be selected.  The special price and an optional start/end date are also entered in this window. 

![Specials from list](/images/specials_from_list.png)

When selection from a list is used, the same window is shown, but instead of providing a list for product selection, the product is shown as an un-editable value.   The other fields are the same. 

![Specials by ID](/images/specials_by_id.png)

Specials are displayed in your store in the specials sidebox, in a centerbox and on the specials page.  To learn more, read about [how specials are handled on the storefront](/user/products/special_products/). 

Specials may optionally apply to the attribute prices when products have priced attributes.  When such products are put on special, the flag **Apply Discounts Used by Product Special/Sale** in the [attributes controller](/user/admin_pages/catalog/attributes_controller/#attribute-flags) determines whether the special discount is also applied to the attributes price. 
