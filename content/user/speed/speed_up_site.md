---
title: How do I speed up my site? 
description: Basic performance improvement tips 
category: speed
weight: 5 
---


Here are some suggestions, assuming you're running the latest-released version of Zen Cart:  

### Turn off Category Counts, especially if you have a large number of categories.  
Go to [Admin > Config > My Store](/user/admin_pages/configuration/configuration_mystore/) 

    - Show Category Counts = false  
    - Show Category Counts-Admin = false  

    (this second one is for admin-area only when editing catalog)  

### Disable the Manufacturers sidebox if you don't need it.  
Go to [Admin > Tools > Layout Boxes Controller](/user/admin_pages/tools/layout_boxes_controller/). 
    Find the sideboxes/manufacturers.php entry, and turn it "OFF"  

### Disable Products Viewed 
<font color="red">NEW!</font> 
In releases prior to 1.5.7, the Zen Cart "products viewed" feature can cause performance degradation on 
busy sites.  

Disable this feature by editing ` includes/extra_datafiles/products_viewed_counter.php` and setting `LEGACY_PRODUCTS_VIEWED_COUNTER` to `off`.

**NOTE:** This change is only relevant for Zen Cart 1.5.6c and below. 

### Ensure your images are optimized for your site.  

Specifically, use small images for thumbnails, slightly larger for product pages (`_MED` images), and large detailed images for "click to enlarge" (`_LRG`) images.  

See also these articles: 

- [Adding Multiple Images To Products](/user/images/additional_images/) 
- [Preparing and Optimizing Images](/user/images/images_howto/) 

### Disable unused attribute settings 
In [Admin > Configuration > Attribute Settings](/user/admin_pages/configuration/configuration_attributesettings/), there are a few switches which, if turned off, will reduce the number of queries used to calculate and display product information:  

- Enable Downloads -- If you're not doing downloads on your site, turn this off.  
- Enable Price Factor -- If you're not using price-by-attributes support, turn this off to stop those calculations and the related queries  
- Enable Qty Price Discount -- If you're not doing quantity discounts, turn this off  
- Enable Attribute Images -- If you're not adding images to your attributes, turn this off  
- Enable Text Pricing by word or letter -- If you're not offering text attributes which calculate per-word or per-letter, turn this off.  

- In the [Attributes Controller](/user/admin_pages/catalog/attributes_controller/), when you are adding an attribute to a product, set "Apply Discounts Used by Product Special/Sale: No" (assuming that the options don't have cost associated with them); this will heavily reduce your parse times.  

### Home Page performance 
If it's primarily your home page (ie: the storefront) that's slow, you might consider turning off content-boxes related to specials and featured products, as they generate a lot of extra queries to extract special pricing information.  

### Don't overload categories 
 If your categories contain a LOT of products, consider dividing them into subcategories for improved efficiency not only in performance but also in helping the customer find what they're looking for.  

If you really can't make your categories more lean, consider turning off the previous/next buttons on the [Admin > Configuration > Product Info](/user/admin_pages/configuration/configuration_productinfo/) page, or at least set the prev/next sort mode to NOT include the product name (ie: pick product Model or Price instead).  

Further, when you have a LOT of products in large numbers of subcategories, you may find significant improvement by going to [Admin > Configuration > Index Listing](/user/admin_pages/configuration/configuration_indexlisting/) and turning off the first 8 settings there (setting them to 0). Adjust as necessary, depending on what content you wish to display.  

### Reduce New Products window 
The "new products" selection window is by default set to "Forever". The configuration setting  [Admin > Configuration > Maximum Values > New Product Listing - Limited to ...](/user/admin_pages/configuration/configuration_maximumvalues/) tells the system how far back to look when creating a list of new products. [Setting the new product timeframe to a smaller window](/user/admin/what_is_new/) will make the display of "new products" (in sideboxes and center content-boxes) run much faster, and thus improve speed.  

### Disable Also Purchased Products 

The [Also Purchased Products](/user/template/also_purchased/) display on the product info page is an expensive
query when the orders table is large. Try setting [Also Purchased Products Columns per Row](/user/admin_pages/configuration/configuration_productinfo/#also_purchased_products_columns_per_row) to 0 to disable this feature, and see if that noticeably increases the speed of your product pages.

### Consider GZip Compression
In some cases, enabling gzip compression can be helpful for people experiencing slowness loading a site over slow internet connections:  
Go to [Admin > Config > GZip Compression](/user/admin_pages/configuration/configuration_gzipcompression/) and set Enable GZip Compression = 1  

### Ensure Images Exist 
Ensure that your stylesheets don't contain any references to image files that don't exist on your server. (You can use the [Website Optimizer Speed Test](http://www.websiteoptimization.com/services/analyze/index.html) site to quickly find missing images on specific pages.)  

### Remove Excess debug/log files
If your site has generated a large number of [debug log files](/user/troubleshooting/debug_logs/), it can cause some degree of slowdown. (This is worsened if you're using v1.5.0 or older, where those log files are stored on the /cache/ folder. Having a lot of non-caching files in the /cache/ folder can lead to serious slowdowns on all versions.)  

You will want to download a copy of those log files to your PC, using your [FTP tool](/user/first_steps/useful_tools/#ftp-tools). Then analyze them to see what errors might be occurring on your site on a regular basis.  
Then you can purge those logs files by using the [Admin > Tools > Store Manager](/user/admin_pages/tools/store_manager/) Purge log files menu option.  

### Use MySQL slow query log 
Use the MySQL slow query log feature to identify poorly-performing database queries.  

You may need to talk to your hosting company to enable this feature and to evaluate the logs generated. Set it with a low threshold so that you can see where the database is spending its time.  

Do you have any plugins enabled that add their own tables? Maybe they're poorly tuned tables.  

Or have you written any custom code or use any addons which run queries that attempt to join tables on unindexed database columns?  

### Review other settings that can cause slowdowns 

In addition to the settings mentioned above, additional settings you may wish to change to improve performance are as follows: 

- Admin > Configuration > Maximum Values > Manufacturers List - Verify Product Exist
- Admin > Configuration > Sessions > IP to Host Conversion Status

Each of these settings has its own documentation. 

### Consider additional server tuning
Consider these [Webserver Tuning Tips](/user/speed/webserver_tuning/).

### Check for duplicate jQuery libraries 
In case you haven't already considered this, make sure you're not loading more than one copy of jQuery on your site.  

Many plugins come with their own copy of jquery.js or jquery-min.js (or some numbered version of the same pattern), and you shouldn't be loading them all; only load one, and that should be the latest version. 

