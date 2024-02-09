---
title: Columnar Layout for Category Listing pages 
description: Presenting categories in a Grid 
category: template
weight: 10
---

**Note:** This page refers to category listings.  There's a separate page for [product listings](/user/template/listing_columns/).

Zen Cart includes a configuration setting called [Categories To List Per Row](/user/admin_pages/configuration/all/#categories_to_list_per_row/).  This setting allows you to display multiple columns of categories per row on the Category Listing page. 

Consider the default value of 3.  It looks good on a desktop: shows three categories per row.

![Wide window - 3 columns](/images/bs_cat_listing_wide.png)

But on a mobile device, that many won't fit, so it drops to one per row. 

![Phone window - 1 column](/images/bs_cat_listing_phone.png)

## Fluid Mode in Bootstrap
In the Bootstrap template, setting `Categories To List Per Row` to 0 allows the template to determine how many categories will fit on the screen dynamically.  A smaller window will have fewer categories , and a larger window will have more.  Setting `Categories to List Per Row` to 0 is called *fluid mode* in the Bootstrap template.   

Here's a Bootstrap category listing page in fluid mode in a wide window (around 1500px): 

![Wide window - fluid](/images/bs_cat_listing_wide_fluid.png)

And here's what the same page looks like when the window is narrowed to 1024px (iPad width): 

![Tablet window - 3 columns](/images/bs_cat_listing_tablet_fluid.png)

And finally, here's what the same page looks like when the window is narrowed to 500 px (mobile phone): 

![Phone window - 1 column](/images/bs_cat_listing_phone_fluid.png)

The default number of categories per row shown on a mobile device is 1, but I increased it to 2 using the first developer tip below.

**Note:** Your template must also support values 0 for this setting.  Both the Responsive Classic and [Bootstrap](/user/template/bootstrap/) templates do. 

Developer Tips: 
- the number of columns shown at each window size may be adjusted customizing the `$grid_category_classes_matrix` data structure.  Instructions for doing so are provided in `includes/modules/bootstrap/category_row.php`.
- If you are switching back and forth between templates, and want to use rows mode in one and fluid mode in another, consider using the [template_init](/user/template/template_switching/) feature.
- Bootstrap template users may find the [Bootstrap wiki article](https://github.com/lat9/ZCA-Bootstrap-Template/wiki/Frequently-Asked-Questions#configuration--maximum-values--categories-to-list-per-row-display-anomalies) on this topic helpful.
