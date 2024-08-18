---
title: Sort Order for product listing pages
description: Changing how products are sorted on an index listing page
category: customizing 
weight: 10
---

Products shown on a [product listing page](/user/storefront_pages/listing_pages/) are sorted in one of two ways: 

- Using the per-product sort order set on the [product editing](/user/products/product_edit/) page. 
- Using the key [PRODUCT_LISTING_DEFAULT_SORT_ORDER](/user/admin_pages/configuration/configuration_productlisting/#sort_order_default__product_listing) from the Admin > Configuration > Product Listing page.  This key is called "Sort Order Default - Product Listing" in Zen Cart 2.0.0 and above; it was formerly called "Display Product Listing Default Sort Order."

When `PRODUCT_LISTING_DEFAULT_SORT_ORDER` is set to blank, the per-product sort order is used. 

Otherwise, the interpretation is different in Zen Cart 2.0.0 and forward, when compared to older versions of Zen Cart.

## Zen Cart 2.0.0 and forward 
The configuration setting `PRODUCT_LISTING_DEFAULT_SORT_ORDER` may have any of these values: 

#### Sort Order Options Table

|Value|Text String|Meaning| 
|-----|-----|------|
|8|Recommended|ORDER BY p.products_sort_order, pd.products_name (default)|
|1|Product Name|ORDER BY pd.products_name |
|2|Product Name - desc|ORDER BY pd.products_name DESC |
|3|Price - low to high|ORDER BY p.products_price_sorter, pd.products_name |
|4|Price - high to low|ORDER BY p.products_price_sorter DESC, pd.products_name |
|5|Model|ORDER BY p.products_model |
|6|Date Added - New to Old|ORDER BY p.products_date_added DESC, pd.products_name |
|7|Date Added - Old to New|ORDER BY p.products_date_added, pd.products_name|

Note the use of `p.products_price_sorter` rather than `p.products_price` - see 
"Update ALL Products Price Sorter" in [Store Manager](/user/admin_pages/tools/store_manager/).

These values correspond to the sort order dropdown shown on the listing page in 2.0.0 and forward. If an older style value such as "4a" is used in `PRODUCT_LISTING_DEFAULT_SORT_ORDER`, it is overridden to be "8" (Recommended). 

![Listing Page Sort Order Dropdown](/images/listing_page_sort_order.png)

## Zen Cart 1.5.8 and prior 
When `PRODUCT_LISTING_DEFAULT_SORT_ORDER` is non-blank, it is interpreted as follows: 

- There are a list of Display *field name* settings on the Admin > Configuration > Product Listing page.  In 1.5.7, they are: 
  - Display Product Image 
  - Display Product Manufacturer Name
  - Display Product Model
  - Display Product Name 
  - Display Product Price/Add to Cart
  - Display Product Quantity
  - Display Product Weight 

- The settings for each of these values (0 or non-zero) determine whether or not this column will be shown on a product listing page.  For specifics, see 
 [Product Listing Configuration Settings](/user/template/product_listing_page_configuration).

- The configuration settings with non-zero values are ordered according to their setting.  Then the sort is done using the field number specified in the first character of `PRODUCT_LISTING_DEFAULT_SORT_ORDER`, in ascending or descending order according to the second character.  

This is best illustrated by an example.  Consider the following configuration: 

![Listing Page configuration](/images/pl_config_1.png)

<br><br>

This shows that the listing page will display four fields per row, in the following order: 

1. product image
1. product name
1. product price / add to cart 
1. product quantity in stock

If the value of `PRODUCT_LISTING_DEFAULT_SORT_ORDER` is blank, the rows will be sorted according to the per product sort order and product name.   Since frequently per product sort order is zero, this means the products are shown sorted by name, like this: 

![Listing Page sorted by product name](/images/pl_config_2.png)

But if the `PRODUCT_LISTING_DEFAULT_SORT_ORDER` value is 4d, the products are shown sorted by the 4th displayed field (product quantity in stock) in descending order.  The result will look like this: 

![Listing Page sorted by product name](/images/pl_config_3.png)


