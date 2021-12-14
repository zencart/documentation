---
title: Building a Report 
description: Adding a custom report for your needs  
category: code
weight: 10
---

Adding a custom report to your site's admin is a common customization. 

The easiest way to do this is simply to follow one of the built-in examples. 
We'll use the [Products Low Stock](/user/admin_pages/reports/products_low_stock/) report. 

There are two files that make up this report:

- admin/stats_products_lowstock.php
- admin/includes/languages/english/stats_products_lowstock.php

Copy those files to files with names that match the data shown on the report.  For example, if the report is designed to show products with zero weight, call the new files: 

- admin/stats_products_zero_weight.php
- admin/includes/languages/english/stats_products_zero_weight.php

Then edit the new code file `admin/stats_products_zero_weight.php` and change the query to do what you want.  In our case, the query for products with zero weight might be: 

```
            $products_query_raw = "SELECT p.products_id, pd.products_name, p.products_quantity, p.products_type
                                   FROM " . TABLE_PRODUCTS . " p,
                                        " . TABLE_PRODUCTS_DESCRIPTION . " pd
                                   WHERE p.products_id = pd.products_id
                                   AND p.products_weight = 0 
                                   AND pd.language_id = " . (int)$_SESSION['languages_id'] . "
                                   ORDER BY pd.products_name";
```

You may need to make other changes to this file of course depending on your needs. 

Then edit the new language file `admin/includes/languages/english/stats_products_zero_weight.php` and change the title, then make any other appropriate changes.

You can now run your report using the URL 

```
https://MYSTORE.com/MYADMINNAME/index.php?cmd=stats_products_zero_weight
```

but you don't see it in the dropdown Admin > Reports.  Why not? 

The answer is, it needs to be added to the admin pages table, which requires some defined constants.  If you look at any of the [reports in the Plugins area](https://www.zen-cart.com/downloads.php?do=cat&id=1), you'll see how this is done. We will look at [Disabled Products Report](https://www.zen-cart.com/downloads.php?do=file&id=2302) to see one example: 

This report creates a third file called `admin/includes/extra_datafiles/products_disabled.php`.  So create your own file, using the naming convention above, called `admin/includes/extra_datafiles/products_zero_weight.php`.

You'll want the contents to be something like: 

```
<?php
define('FILENAME_ZERO_WEIGHT','stats_products_zero_weight');
define('BOX_REPORTS_ZERO_WEIGHT','Zero Weight Report');
```

Now you have to populate the database with these constants so the system knows to show this option in the Reports dropdown. 

You can provide an external SQL and run it by hand in Admin > Tools > Install SQL Patches, as this report does. 

The query would be something like 

```
INSERT INTO admin_pages (page_key, language_key, main_page, page_params, menu_key, display_on_menu, sort_order) VALUES ('productsZeroWeight', 'BOX_REPORTS_ZERO_WEIGHT', 'FILENAME_ZERO_WEIGHT', '', 'reports', 'Y', 500);
```

alternately, you can run this query in a file in `admin/functions/extra_functions` automatically, to make installing this report easier. It's your choice.
