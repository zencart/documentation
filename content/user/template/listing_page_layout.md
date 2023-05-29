---
title: Listing Page Layout
description: How Zen Cart shows multiple results on one page 
category: template
weight: 10
---

Listing Pages are used to show groups of results.  Examples of listing pages are: 

- New Products 
- Featured Products
- All Products
- Product Listing page for a specific category (Index Listing Page)

There are specific configurations for these pages: 

- The New Products page is configured by [Admin > Configuration > New Listing](/user/admin_pages/configuration/configuration_newlisting/).
- The Featured Products page is configured by [Admin > Configuration > Featured Listing](/user/admin_pages/configuration/configuration_featuredlisting/).
- The All Products page is configured by [Admin > Configuration > All Listing](/user/admin_pages/configuration/configuration_alllisting/).
- Product Listing Pages that show the products in a category are configured by [Admin > Configuration > Product Listing](/user/admin_pages/configuration/configuration_productlisting/).

These four pages are share some of the same layout features: 
- stacked rows with one product per row.  Note that since 1.5.7b, it has been possible to display products in a [grid layout](/user/template/listing_columns/) with multiple columns per row. 
- [paginated results display](/user/template/pagination/) so that only a subset of the total number of results are shown on each page.  Navigation is provided between pages of results. 

Three of the pages, New, Featured, and All Products, have configuration settings that are identical in nature. The full explanation for these display settings can be found here: [New/Featured/All Listing Configuration Settings](/user/template/new_featured_all_listing_page_configuration).

The Product Listing page configuration is a bit different.  A full explanation for its display settings can be found here: [Product Listing Configuration Settings](/user/template/product_listing_page_configuration).


The [Admin > Configuration > Index Listing](/user/admin_pages/configuration/configuration_indexlisting/) configuration settings are actually for Centerboxes, not the Product Listing page.  This is explained in the [Index Listing Configuration](/user/template/index_listing) FAQ. 

### Buy Button Behavior - Index listing page 
The option to buy from the index listing page is controlled by two settings in Configuration > Product Listing page: 

- `Display Product Add to Cart Button` 
- `Display Multiple Products Qty Box Status and Set Button Location`

Assuming all products on the listing page may be added to the cart: 

- if `Display Multiple Products Qty Box Status` is 0 and `Display Product Add to Cart Button` is 1, a "Buy Now" button is shown on the listing page for each product.  Only one of each product may be added at a time. 
- if `Display Multiple Products Qty Box Status` is 0 and `Display Product Add to Cart Button` is 2, an "Add to Cart" button with a quantity box is shown on the listing page for each product. 
- if `Display Multiple Products Qty Box Status` is non-zero, a quantity box is shown for each product on the listing page. At the top and bottom of the page, buttons are provided which add all non-zero quantities of products set on that page. 

### Buy Button Behavior - other listing pages
The option to buy from the New, Featured and All listing pages is controlled by two settings in the specific configuration page shown above: 

- `Display Product Buy Now Button` 
- `Display Multiple Products Qty Box Status and Set Button Location`

Assuming the first config is non-zero, and all products on the listing page may be added to the cart: 

- if `Display Multiple Products Qty Box Status` is zero, and the a "Buy Now" button is shown on the listing page for each product.  Only one of each product may be added at a time. 
- if `Display Multiple Products Qty Box Status` is non-zero, a quantity box is shown for each product on the listing page. At the top and bottom of the page, buttons are provided which add all non-zero quantities of products set on that page. 

