---
title: Product Editing Screen
description: The screen for adding and editing products 
category: products
weight: 10
---

The product editing screen is reached by going to [Admin > Catalog > Categories/Products](/user/admin_pages/catalog/categories/), and then navigating down to [the product level](/user/admin_pages/catalog/categories_products/) and editing a specific product. 

The screen allows you to set all the product fields available to 
that product type.  It is used for both product creation and product editing.

![product editing screen](/images/product_edit.png)

The fields in the `Product - General` product type that can be set 
when adding or editing a product are: 

- Master Category - the category for the product. The product may also be in other categories using the [linked categories](/user/products/linked_product/) feature. 
- [Products Status](/user/products/products_status/) - set to Disabled to not display in the storefront; Enabled otherwise
- [Date Available](/user/products/upcoming_products/) - use if the product will not be available until the future
- Products Manufacturer - select a [manufacturer](/user/admin_pages/catalog/manufacturers/) if you organize products by manufacturer
- Products Name - title for the product 
- Product is Free - Yes if so. 
- Product is Call for Price - when used, the product will not be directly purchasable
- [Product Priced by Attributes](/user/products/attribute_pricing/) - is the product's price determined by its attribute settings?  
- Tax Class - if taxes are applicable, which ones? 
- Products Price (Net) - base price of product before taxes 
- Products Price (Gross) - computed using net price plus applicable taxes if the product was shipped to the location specified Admin > Configuration > My Store > Zone.  (Think: if my store offered pickup, what taxes would I need to charge?)
- Wholesale Price - Since Zen Cart 2.0.0, if [wholesale pricing](/user/products/wholesale_pricing) is enabled, the wholesale price is set here. 
- Product is Virtual - is the product a completely digital item 
- Always Free Shipping - does the product ship for free? 
- Products Quantity Box Shows - whether to show the quantity box on pages which allow the product to be purchased, such as [product info](/user/products/product_info) page. Note that **not** showing the quantity box on a product page will also disable the option to update that product's quantity in the shopping cart.  
- [Product Qty Minimum](/user/products/product_units/) - lowest number of this product which may be purchased 
- [Product Qty Maximum](/user/products/product_units/) - highest number of this product which may be purchased 
- [Product Qty Units](/user/products/product_units/) - if > 1, this product must be purchased in bundles of this many 
- [Product Qty Min/Unit Mix](/user/products/mixed_on/) - can products with different attributes be combined to reach the Product Qty Minimum threshold? 
- Products Description - details about the product 
- Products Quantity - quantity in inventory 
- [Products Model](/user/products/product_model/) - model number or SKU 
- Products Image - main photo for product 
- Products URL - if there is another web page that provides more information, add the URL here 
- Products Shipping Weight - weight before adding packing materials 
- Length, Width and Height: Since Zen Cart 2.0.0 it has been possible to add [product dimensions](/user/shipping/shipping_dimensions/) to a product.
- Ships in Own Box: Since Zen Cart 2.0.0 it has been possible to specify products that ship in their own box.  See [product dimensions](/user/shipping/shipping_dimensions/).  Note that these products do not incur additional tare weight.See [How Weight and Tare Are Determined](/user/shipping/shipping_calculations/) for more details. 
- Sort Order - the order the product will be displayed in on a [listing page](/user/products/product_listing/). 

For more information, see the [product FAQs](/user/products/). 

