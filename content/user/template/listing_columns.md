---
title: Columnar Layout for Product Listing pages 
description: Presenting products in a Grid 
category: template
weight: 10
---

**Note:** This page refers to product listings.  There's a separate page for [category listings](/user/template/listing_columns_categories/).

Since 1.5.7, Zen Cart includes a configuration setting called [Columns Per Row](/user/admin_pages/configuration/configuration_productlisting/#columns_per_row).  This setting allows you to display multiple columns of products per row on the Product Listing page. 

**Note:** Your template must also support this setting.  Both the Responsive Classic and [Bootstrap](/user/template/bootstrap/) templates support this setting.  Many older templates use a version of the Column Grid Layout plugin, which is deprecated by this setting.

This is what it looks like when `Columns Per Row` is set to 3.
![3 Columns per Row](/images/listing_col_3.png)

<br>

This is what it looks like when `Columns Per Row` is set to 1.  Using this setting is called *rows mode*. 

![1 Column per Row](/images/listing_col_1.png)

**Version Difference**
- In Zen Cart 2.x.x, `Columns Per Row` applies to all listing pages.  See [listing page configuration](/user/template/product_listing_page_configuration/). 
- In Zen Cart 1.x.x, `Columns Per Row` only applies to Product Listing pages, not other listing pages such as All Products or New Products. See  [new/featured/all products listing page configuration in v1.x.x](/user/template/new_featured_all_listing_page_configuration_v1/).

## Fluid Mode in Bootstrap
In the Bootstrap template, the recommended value of `Columns Per Row` is 0, which allows the template to determine how many columns will fit on the screen dynamically.  A smaller window will have fewer columns, and a larger window will have more.  

Setting `Columns Per Row` to 0 is called *fluid mode* in the Bootstrap template.   The Bootstrap template is best run in either rows mode or fluid mode.

Here's a Bootstrap listing page in fluid mode in a wide window (around 1500px): 

![Wide window - 4 columns](/images/bs_listing_wide.png)

And here's what the same page looks like when the window is narrowed to 1024px (iPad width): 

![Tablet window - 3 columns](/images/bs_listing_tablet.png)

And finally, here's what the same page looks like when the window is narrowed to 500 px (mobile phone): 

![Phone window - 1 column](/images/bs_listing_phone.png)

Developer Tips: 
- the number of columns shown at each window size may be adjusted customizing the `$grid_classes_matrix` data structure.  Instructions for doing so are provided in `includes/modules/bootstrap/product_listing.php`.
- If you are switching back and forth between templates, and want to use rows mode in one and fluid mode in another, consider using the [template_init](/user/template/template_switching/) feature.


