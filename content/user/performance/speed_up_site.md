---
title: How do I speed up my site? 
description: Performance for Zen Cart 
category: performance
weight: 10
---


FIXME link to admin_pages 

Here are some suggestions, assuming you're running the latest-released version of Zen Cart:  

1\. Turn off Category Counts, especially if you have a large number of categories.  
a. Admin->Config->My Store->Show Category Counts=false  
b. Admin->Config->My Store->Show Category Counts-Admin = false  
(this second one is for admin-area only when editing catalog)  

2\. Disable the Manufacturers sidebox if you don't need it.  
Admin->Tools->Layout Boxes Controller  
- find the sideboxes/manufacturers.php entry, and turn it "OFF"  

3\. Ensure your images are optimized for your site... specifically, use small images for thumbnails, slightly larger for product pages (`_MED` images), and large detailed images for "click to enlarge" (`_LRG`) images.  

Related FAQ articles:  
- [Adding Multiple Images To Products](/user/products/images_multiple/) 
- [Preparing and Optimizing Images](/user/products/images_howto) 

4\. In Admin->Configuration->Attribute Settings, there are a few switches which, if turned off, will reduce the number of queries used to calculate and display product information:  
- Enable Downloads -- If you're not doing downloads on your site, turn this off.  
- Enable Price Factor -- If you're not using price-by-attributes support, turn this off to stop those calculations and the related queries  
- Enable Qty Price Discount -- If you're not doing quantity discounts, turn this off  
- Enable Attribute Images -- If you're not adding images to your attributes, turn this off  
- Enable Text Pricing by word or letter -- If you're not offering text attributes which calculate per-word or per-letter, turn this off.  

4 (b). In your individual attribute assignments, set "Apply Discounts Used by Product Special/Sale: No" (assuming that the options don't have cost associated with them); this will heavily reduce your parse times.  

5\. If it's primarily your home page (ie: the storefront) that's slow, you might consider turning off content-boxes related to specials and featured products, as they generate a lot of extra queries to extract special pricing information.  

6\. If your categories contain a LOT of products, consider dividing them into subcategories for improved efficiency not only in performance but also in helping the customer find what they're looking for.  
If you really can't make your categories more lean, consider turning off the previous/next buttons on the product-info page (Admin->Configuration->Product Info), or at least set the prev/next sort mode to NOT include the product name (ie: pick product Model or Price instead).  

Further, when you have a LOT of products in large numbers of subcategories, you may find significant improvement by going to Admin->Configuration->Index Listing and turning off the first 8 settings there (setting them to 0). Adjust as necessary, depending on what content you wish to display.  

7\. The "new products" selection window is by default set to "Forever". [Setting this to a smaller window](/user/admin/admin_misc/#what-determines-if-a-product-is-new) will make the display of "new products" (in sideboxes and center content-boxes) run much faster, and thus improve speed.  

8\. In some cases, enabling gzip compression can be helpful for people experiencing slowness loading a site over slow internet connections:  
Admin->Config->GZip Compression->Enable GZip Compression = 1  

9\. Ensure that your stylesheets don't contain any references to image files that don't exist on your server. (You can use the [Website Optimizer Speed Test](http://www.websiteoptimization.com/services/analyze/index.html) site to quickly find missing images on specific pages.)  

10\. Excess debug/log files.  
If your site has generated a large number of debug log files, it can cause some degree of slowdown. (This is worsened if you're using v1.5.0 or older, where those log files are stored on the /cache/ folder. Having a lot of non-caching files in the /cache/ folder can lead to serious slowdowns on all versions.)  
You will want to download a copy of those log files to your PC, using your FTP program. Then analyze them to see what errors might be occurring on your site on a regular basis.  
Then you can purge those logs files by using the Admin->Tools->Store Manager->Purge log files menu option.  

11\. Assess [Page Parse Times](/user/performance/page_parse_times) to isolate where your bottleneck is occurring.  

12\. Use the MySQL slow query log feature to identify poorly-performing database queries.  
You may need to talk to your hosting company to enable this feature and to evaluate the logs generated. Set it with a low threshold so that you can see where the database is spending its time.  
Do you have any mods enabled that add their own tables? Maybe they're poorly tuned tables.  
Or have you written any custom code or use any addons which run queries that attempt to join tables on unindexed database columns?  

13\. Consider these [Webserver Tuning Tips](/user/performance/webserver_tuning).

14\. In case you haven't already considered this, make sure you're not loading more than one copy of jQuery on your site.  

Many plugins come with their own copy of jquery.js or jquery-min.js (or some numbered version of the same pattern), and you shouldn't be loading them all!!!  

Rule of thumb: Only load one! And usually that should be the newest version.</font>
