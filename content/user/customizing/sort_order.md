---
title: Sort Order for product listing pages
description: Changing how products are sorted on an index listing page
category: customizing 
weight: 10
---

Products shown on a [product listing page](/user/storefront_pages/listing_pages/) are sorted in one of two ways: 

- Using the per-product sort order set on the [product editing](/user/products/product_edit/) page. 
- Using the value [PRODUCT_LISTING_DEFAULT_SORT_ORDER](/user/admin_pages/configuration/configuration_productlisting/#display_product_listing_default_sort_order) from the Admin > Configuration > Product Listing page.

When `PRODUCT_LISTING_DEFAULT_SORT_ORDER` is set to blank, the per-product sort order is used. 

When it is non-blank, it is interpreted as follows: 

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


