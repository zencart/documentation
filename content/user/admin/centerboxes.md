---
title: New/Featured/Special/Upcoming Products sections
description: Zen Cart Centerbox enable / disable
category: admin
weight: 10
---

[Centerboxes](/user/template/centerboxes/)
are pieces of content that are displayed in the middle of the screen in the Zen Cart storefront.  Some places you might see them are on the Index page or the Shopping Cart page. 

This article is about controlling centerboxes from the admin. 

As the title of this article suggests, Zen Cart has these built-in Centerboxes, which have admin controls: 

- New Products 
- Featured Products
- Special Products
- Upcoming Products

Newer versions have more centerboxes: 
- Featured Categories (added in Zen Cart 2.1.0)

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
| The number of items in the Featured Products centerbox | Maximum Display of Featured Products - Main Page | Featured Products Centerbox <br>Featured Products And Categories Centerbox (2.1.0 and higher)|
|The number of items in the Special Products centerbox |Maximum Display of Specials Products - Main Page |Products on Special Centerbox|
|The number of items in the Upcoming Products centerbox | Upcoming Products |Upcoming Products Centerbox |
|The number of items in the Featured Categories centerbox | N/A | Featured Products And Categories Centerbox (2.1.0 and higher)|

In addition to the centerboxes discussed above, the following centerboxes are available:

- The [Also Purchased](/user/template/also_purchased) centerbox may be displayed on the product info page using the setting "Also Purchased Products Columns per Row" on [Admin > Configuration > Product Info](/user/admin_pages/configuration/configuration_productinfo/).

- The [Cross Sell Advanced](/user/products/xsell) plugin creates its own centerbox, which is displayed on the product info page.
