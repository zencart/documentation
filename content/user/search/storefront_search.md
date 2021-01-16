---
title: Storefront search
description: How customers can search your store
category: search 
weight: 10
---


There are two sideboxes which permit your visitors to search your store - the `search.php` sidebox (shown left) and the `search_header.php` sidebox (on the right).  The former is designed to be shown on the left or right sidebar, where the latter is designed for positioning in the store's header. 

<br>
<div style="float: left;">
  <div style="float: left; margin-right: 10px;">
    <img alt="Search Sidebox" src="/images/sidebox_search.png" />
  </div>
  <div style="float: left;">
    <img alt="Search Header Sidebox" src="/images/sidebox_search_header.png" />
  </div>
</div>
<br clear="all">
<br>

The link in the `search.php` sidebox to the Advanced Search page goes to a screen that looks like this: 

## Advanced Search Page

![Advanced Search](/images/advanced_search.png)

The advanced search page allows visitors to narrow their search to only specific categories, manufacturers, price ranges, and product creation dates. This can be useful for stores with a large number of SKUs. 

The contents of the `keywords` field is used to search the following fields: 

Table | Fields 
------|-------
products | products_model 
products_description | products_description [^1] 
manufacturers | manufacturers_name
meta_tags_products_description | metatags_description [^2]


[^1]: if the `Search in Product Descriptions` checkbox is checked, or if the search is done from one of the search sideboxes. 
[^2]: if the configuration setting [Include meta-tags in product search?](/user/admin_pages/configuration/configuration_mystore/#include_metatags_in_product_search) is set to `true`.  

You can see [the database schema](/dev/schema/) if you wish to learn more about how the database is structured. 

The _Search in Product Descriptions_ checkbox is provided because sometimes searching the product description produces false positive search results.   

If the configuration setting [SKIP_SINGLE_PRODUCT_CATEGORIES](/user/admin_pages/configuration/configuration_layoutsettings/#skip_1prod_categories) is true, and a search returns a single value, the product listing page will be bypassed and the product info page will be displayed for the resulting product. 
