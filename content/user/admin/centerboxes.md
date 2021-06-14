---
title: New/Featured/Special/Upcoming Products sections
description: Zen Cart Centerbox enable / disable
category: admin
weight: 10
---

[Centerboxes](/user/template/centerboxes/)
are pieces of content that are displayed in the middle of the screen in the Zen Cart storefront.

This article is about controlling centerboxes from the admin. 

As the title of this article suggests, there are four built-in Centerboxes: 

- New Products 
- Featured Products
- Special Products
- Upcoming Products

Each of these blocks can be displayed on a number of pages. Using the New Products centerbox as an example, the following settings exist:

On [Admin > Configuration > Stock](/user/admin_pages/configuration/configuration_stock/), 

- Show New Products on empty Shopping Cart Page

On [Admin > Configuration > Index Listing](/user/admin_pages/configuration/configuration_indexlisting/), 
- Show New Products on Main Page
- Show New Products on Main Page - Category with SubCategories
- Show New Products on Main Page - Errors and Missing Products Page
- Show New Products - below Product Listing

For each of these values: 

- The values you set are the Sort Order of the Centerboxes 
- Turn OFF by setting to 0 all of the ones you do NOT want to see displayed 

Once you have turned on a centerbox and determined its position, you must decide how many items it should contain.

The number of products shown in each centerbox is controlled using settings from [Admin > Configuration > Maximum Values](/user/admin_pages/configuration/configuration_maximumvalues/).  Note that names of these settings changed in Zen Cart 1.5.8.

For example: 

| Purpose | Pre-1.5.8| 1.5.8 and higher| 
|---------|----------|-----------|
|The number of items in the New Products centerbox |New Products Module | New Products Centerbox|
| The number of items in the Featured Products centerbox | Maximum Display of Featured Products - Main Page | Featured Products Centerbox|
|The number of items in the Special Products centerbox |Maximum Display of Specials Products - Main Page |Products on Special Centerbox|
|The number of items in the Upcoming Products centerbox | Upcoming Products |Upcoming Products Centerbox |

