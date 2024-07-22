---
title: Product Listing configuration settings
description: Configuration for Product Listing pages 
category: template 
weight: 10
---

The Product Listing (or Index Listing) pages are [listing pages](/user/storefront_pages/listing_pages/) showing all products in a specific category. 

These pages have their own configuration settings page, which is described in 
[Admin > Configuration > Product Listing](/user/admin_pages/configuration/configuration_productlisting/).

On this page, the top settings are:

  - Display Product Image 
  - Display Product Manufacturer Name
  - Display Product Model
  - Display Product Name 
  - Display Product Price/Add to Cart
  - Display Product Quantity
  - Display Product Weight 

Each of these values is set the same way, with a zero (indicating do not display this field on the listing page) or a positive number (indicating display this field in this order). 

There are two things about the display of index listing pages that can be changed using admin controls: 

a) How products are sorted when displayed on an index listing page:

By default, the sort order of products is done according to the sort order field on the products editing page. 

This can be changed using [Display Product Listing Default Sort Order](/user/admin_pages/configuration/configuration_productlisting/#display_product_listing_default_sort_order) on the Admin > Configuration > Product Listing page.  See [sort order](/user/customizing/sort_order/) for more details. When this value is set, one of the fields above (name, price, quantity, etc.) will be used to sort the products. 

In the storefront, it can also be changed using the Sort Order dropdown. 

In Zen Cart 2.0.0 and above, the values for Display Product Listing Default Sort Order correspond to the options shown in this dropdown, as shown in [this table](/user/customizing/sort_order/#sort-order-options-table).

![Listing Page Sort Order Dropdown](/images/listing_page_sort_order.png)

In Zen Cart 1.5.8 and below, the values for Display Product Listing Default are explained [here](/user/customizing/sort_order/#zen-cart-158-and-prior).

b) How each product is displayed on the listing page.

The "Display" controls described above indicate whether a particular field is shown for a product.  The layout in which they are shown has three columns per row of listed products: 

- the image is on the left 
- the price and add to cart box is on the right
- in the center are product name, model, manufacturer, description, quantity and weight. 

This behavior may be modified by changing the template file `includes/modules/YOURTEMPLATE/product_listing.php`.

In Zen Cart 1.x.x, the New Products, Featured Products, All Products and Specials pages are configured differently - see [New Listing - Featured Listing - All Listing configuration settings for Zen Cart v1.x.x](/user/template/new_featured_all_listing_page_configuration_v1/). 

Note that since Zen Cart 2.0.0, the New Products, Featured Products, All Products and Specials pages have been configured the same as product listing pages.  See [Listing Configuration Settings](/user/template/new_featured_all_listing_page_configuration/).

