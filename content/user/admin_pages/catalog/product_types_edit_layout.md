---
title: Product Types ≫ Layout Settings
category: admin_pages
weight: 21
---

Zen Cart is flexible enough to allow multiple product types so that stores with special needs can create a custom product with the required data fields and behaviors. However, the most common product type is `Product - General`, and this is the only product type that most stores use.  

Each [product type](/user/admin_pages/catalog/product_types/) can choose to show or hide specific fields. 

The Product Types Layout Settings page has a series of flags that allow you to enable or disable the fields that are shown on the Product Info page *for the currently selected product type*.   These augment the product-type-independent fields which are set on Admin > Configuration > Layout Settings. 

![Layout Settings page](/images/layout_settings.png)

For example: 

- To turn off the display of Model number, click `Show Model Number`, click the dropdown and select `False`, and then press `Update`.

There are also settings that control the meta data which is shown on the product info page.  For example: 

- To turn off the inclusion of product price in the `<title>` tag, click `Product page <title> tag - default: use Product Price`, click the dropdown and select `False`, and then press `Update`.

### Issue: I am turning off the display of fields in Layout Settings, but they are still displayed on my product info page. 

This can occur when template authors choose not to respect the flags that Zen Cart uses.  To fix this, edit `includes/templates/YOURTEMPLATE/templates/tpl_product_info_display.php` and modify the code that handles the display of the field you wish to turn off. 

If you are a developer, see [technical information on product types](/dev/code/product_types/). 

### Issue: I have suppressed the display fields on the Product Info page, but they are still showing on the listing pages.

#### Guidance for Zen Cart v2.x.x: 
The switches for New, All and Featured listing pages, as well as 
the switches for the [Product Listing pages](/user/storefront_pages/product_listing/) are provided on the [product listing configuration page](/user/admin_pages/configuration/configuration_productlisting/) in Admin > Configuration > Product Listing. 

#### Guidance for Zen Cart v1.x.x: 
There are separate switches for the New, All and Featured listing pages, which are shown in [new/featured/all products listing page configuration](/user/template/new_featured_all_listing_page_configuration/). 

The switches for the [Product Listing pages](/user/storefront_pages/product_listing/)  are provided on the [product listing configuration page](/user/admin_pages/configuration/configuration_productlisting/) in Admin > Configuration > Product Listing. 

