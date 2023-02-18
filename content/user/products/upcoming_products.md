---
title: Upcoming Products
description: Products that will be available in the future 
category: categories
weight: 10
---

Upcoming Products are those whose _Date Available_ setting on the 
[product editing page](/user/products/product_edit/) is set to a date in the future. 

If you have created upcoming products, Zen Cart allows you to show them 
in a [Centerbox](/user/template/centerboxes/)
on the main page called Upcoming Products.  This can be configured with the setting *Show Upcoming Products on Main Page* in [Admin > Configuration > Index Listing](/user/admin_pages/configuration/configuration_indexlisting/) setting. 

You may also configure upcoming products to appear in the following places: 

- in a centerbox on an empty shopping cart page with the setting *Show Upcoming Products on Main Page* on [Admin > Configuration > Stock](/user/admin_pages/configuration/configuration_stock/)
- in a centerbox below a [product listing page](/user/storefront_pages/listing_pages/) using the settings on [Admin > Configuration > Index Listing](/user/admin_pages/configuration/configuration_indexlisting/)

Some stores will set the [products status](/user/products/products_status/) of an upcoming product to Disabled until the release date is reached.  In this case, a storeowner may wish to automate the transition to products status Enabled by using the [enable disabled product by available date](/user/admin_pages/configuration/configuration_stock/#enable_disabled_product_by_available_date) feature, which has been available since Zen Cart 1.5.7. Otherwise, moving a product to enabled must be done using the Admin panel or perhaps a cron job. 

**Note:** Upcoming Products were called "Products Expected" in releases prior to v1.5.8.

## Related 

- [Upcoming Products Admin Screen](/user/admin_pages/catalog/products_expected/)
- [how to enable/disable the Upcoming Products section](/user/admin/centerboxes/)
- [Enable disabled product by available date](/user/admin_pages/configuration/configuration_stock/#enable_disabled_product_by_available_date)

 
