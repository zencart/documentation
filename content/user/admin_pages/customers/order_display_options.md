---
title: Order Display Options 
category: admin_pages
weight: 100 
---

The Orders, Invoice and PackingSlip pages have features that may be enabled or disabled depending on your preferences and the regulatory requirements where you operate. 

To modify these settings, set up your [Admin site specific overrides](/user/admin/site_specific_overrides/) file with these entries:

## Orders Page 

The following flags may be set for the Orders page: 

Flag | Default | Behavior 
-----|---------|---------
`$quick_view_popover_enabled` | false | Enables clickable icon on order listing to show order contents 
`$includeAttributesInProductDetailRows` | true | Shows attributes in popover 
`$show_product_tax` | true | Shows tax columns 
`$show_zone_info` | true | Shows zone where the order was shipped 

## Invoice Page 

The following flags may be set for the Invoice page: 

Flag | Default | Behavior 
-----|---------|---------
`$show_product_images` | true | Display product images on invoice
`$show_attrib_images` | true | Display attribute images on invoice 

## Packingslip Page 

The following flags may be set for the Packingslip page: 

Flag | Default | Behavior 
-----|---------|---------
`$show_product_images_pack` | true | Display product images on packingslip 
`$show_attrib_images_pack` | true | Display attribute images on packingslip 

Note `$show_product_images_pack` and `$show_attrib_images_pack` were added in Zen Cart 1.5.8a.  The initial release of Zen Cart 1.5.8 did not include `$show_product_images_pack` and `$show_attrib_images_pack` but simply overloaded the two variables `$show_product` and `$show_attrib_images` to cover both the Invoice and Packingslip.  

