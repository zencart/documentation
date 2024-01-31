---
title: New Listing - Featured Listing - All Listing configuration settings
description: Configuration for New Products, Featured Products and All Products pages 
category: template 
weight: 10
---

Please note: This content is for Zen Cart 2.x.x.  For Zen Cart version 1.x.x, please see [New Listing - Featured Listing - All Listing configuration settings for Zen Cart v1.x.x](/user/template/new_featured_all_listing_page_configuration_v1/).

The New Products, Featured Products, Specials, and All Products pages are [listing pages](/user/storefront_pages/listing_pages/).  

In v2.x.x, they are all configured the same way [product listing](/user/storefront_pages/product_listing/) pages are, using the settings described in the [product listing configuration page](/user/template/product_listing_page_configuration/). 

Upgraders from v1.x.x please note the following: 
- Specials/New/All/Featured pages now use the same product-listing template as the category navigation does.
- The default behavior of the Specials page has changed from a grid layout to whatever is configured in the [Columns Per Row](/user/template/listing_columns/) setting.
- All these pages will also follow the setting for "columns per row", so if the product-listing uses rows, so will S/N/A/F pages; likewise, if set to 3 columns, all pages will use 3 columns. 
- The old "click column headings for sort" is replaced by the sort dropdown.
- The old configuration settings are available but hidden, so older templates will continue to work. 
- Pagination is not changed.

