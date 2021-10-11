---
title: Columnar Layout for Product Listing pages 
description: Presenting products in a Grid 
category: template
weight: 10
---

Since 1.5.7, Zen Cart includes a configuration setting called [Columns Per Row](/user/admin_pages/configuration/configuration_productlisting/#columns_per_row).  This setting allows you to display multiple columns of products per row on the Product Listing page. 

**Note:** Your template must also support this setting.  Both the Responsive Classic and [Bootstrap](/user/template/bootstrap/) templates support this setting.  Many older templates use a version of the Column Grid Layout plugin, which is deprecated by this setting.

This is what it looks like when `Columns Per Row` is set to 3.
![3 Columns per Row](/images/listing_col_3.png)

<br>

This is what it looks like when `Columns Per Row` is set to 1.  Using this setting is called *rows mode*. 

![1 Column per Row](/images/listing_col_1.png)


Note that the setting `Columns Per Row` only applies to Product Listing pages, not other listing pages such as All Products or New Products.

In the Bootstrap template, the recommended value of `Columns Per Row` is 0, which allows the template to determine how many columns will fit on the screen dynamically.  A smaller window will have fewer columns, and a larger window will have more.  

Setting `Columns Per Row` to 0 is called *fluid mode* in the Bootstrap template.   The Bootstrap template is best run in either rows mode or fluid mode.

Here's a Bootstrap listing page in fluid mode in a wide window (around 1500px): 

![Wide window - 4 columns](/images/bs_listing_wide.png)

And here's what the same page looks like when the window is narrowed to 1024px (iPad width): 

![Tablet window - 3 columns](/images/bs_listing_tablet.png)

And finally, here's what the same page looks like when the window is narrowed to 500 px (mobile phone): 

![Tablet window - 1 column](/images/bs_listing_phone.png)

Developer Tip: the number of columns shown at each window size may be adjusted by editing `includes/modules/bootstrap/product_listing.php` and modifying for `$grid_classes_matrix`.

