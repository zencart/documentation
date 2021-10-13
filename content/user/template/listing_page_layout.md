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
- Product Listing page for category 3

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


The [Admin > Configuration > Index Listing](/user/admin_pages/configuration/configuration_indexlisting/) configuration settings are actually for Centerboxes, not the Product Listing page.  It is explained in the [Index Listing Configuration](/user/template/index_listing) FAQ. 


