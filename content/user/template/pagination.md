---
title: Pagination in Zen Cart 
description: How do display a large number of results? 
category: templates
weight: 10 
---

When a [listing page](/user/template/listing_page_layout/) is created, the results are shown in paginated blocks, with navigation between blocks of results. For example, here's the Specials page on a mobile device.

![Specials pagination](/images/specials_pagination.png)

<br><br>

In this screenshot, there are 27 specials, which are displayed in groups of 9.  The navigation controls (**Next** and **Previous** links) may be shown at the top, bottom or both places. 

The desktop display is similar, but because a desktop screen is wider, more products per row can be shown. 


![Specials pagination - desktop](/images/specials_pagination_desktop.png)

<br><br>

Pagination controls are provided in the Zen Cart admin on the page [Admin > Configuration > Maximum Values](/user/admin_pages/configuration/configuration_maximumvalues/): 

Page Name | Control 
----------|------- 
Specials  | Products on Special
New Products | New Products Listing- Number Per Page 
Featured Products | Maximum Display of Featured Products Page
Advanced Search Results | Products Listing- Number Per Page 
Index Listing | Products Listing- Number Per Page 
All Products | Maximum Display of Products All Page 

<br><br>

The behavior and appearance of the **Next** and **Previous** links is controlled using settings on the [Admin > Configuration > Product Info](/user/admin_pages/configuration/configuration_productinfo/) page. 

