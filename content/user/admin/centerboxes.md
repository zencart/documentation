---
title: New/Featured/Special/Upcoming Products sections
description: Zen Cart Centerbox enable / disable
category: admin
weight: 10
---

This article is about controlling centerboxes from the admin. 

There is a "New Products" section on several pages, including Home Page, New-Products page, All-Products Page, (empty) Shopping Cart page, etc.  These sections are called [centerboxes](/user/template/centerboxes/).

As the title of this article suggests, there are four built-in Centerboxes: 

- New Products 
- Featured Products
- Special Products
- Upcoming Products

The pages where the centerboxes are displayed each have a group of centerbox settings. 

When you go to [Index Listing](/user/admin_pages/configuration/configuration_indexlisting/) under Admin > Configuration, you will see options like:

- Show New Products on Main Page
- Show Featured Products on Main Page
- Show Special Products on Main Page
- Show Upcoming Products on Main Page

For each of these values: 

- The values you set are the Sort Order of the Centerboxes 
- Turn OFF by setting to 0 all of the ones you do NOT want to see displayed 

The same is true on other similar configuration menus under Admin > Configuration:

- [New Listing](/user/admin_pages/configuration/configuration_newlisting/)
- [Featured Listing](/user/admin_pages/configuration/configuration_featuredlisting/)
- [All Listing](/user/admin_pages/configuration/configuration_alllisting/) 

For setting up the Centerboxes of the Empty Shopping Cart, use the settings on the Admin > Configuration > Stock, you will see the settings for:

- Show New Products on empty Shopping Cart Page
- Show Featured Products on empty Shopping Cart Page
- Show Special Products on empty Shopping Cart Page
- Show Upcoming Products on empty Shopping Cart Page

The number of products shown in each centerbox is controlled using settings from [Admin > Configuration > Maximum Values](/user/admin_pages/configuration/configuration_maximumvalues/).  

For example: 

- The number of New Products displayed is controlled by MAX_DISPLAY_NEW_PRODUCTS. 
- The number of Featured Products displayed is controlled by MAX_DISPLAY_PRODUCTS_FEATURED_PRODUCTS.
- The number of Special Products displayed  is controlled by MAX_DISPLAY_SPECIAL_PRODUCTS. 
- The number of Upcoming Products displayed is controlled by MAX_DISPLAY_UPCOMING_PRODUCTS.


