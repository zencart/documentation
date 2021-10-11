---
title: Index Listing Configuration 
description: Configuring product listing pages and associated centerboxes
category: template
weight: 10
---

*Admin > Configuration > Index Listing* doesn't control a row and column layout like the [listing page layout](/user/template/listing_page_layout/) pages for *New Products* and *Featured Products*. Instead, the **Index Listing** settings control location, sort order, number of products per row and category filtering for the  [**centerboxes**](/user/template/centerboxes/) only.

The listing pages do have other configuration settings listed under *Admin > Configuration* but those listings are for the pages only and not the centerboxes. The <span style="color:red">red arrows</span> below point to the configuration settings for the actual pages with these urls: 

- `index.php?main_page=featured_products` 
- `index.php?main_page=products_new`
- `index.php?main_page=index&cPath=...`

The <span style="color:blue;">blue arrow</span>, however, points to the **Index Listing** which only controls the *centerboxes*.

![Configuration Dropdown Menu](/images/config_dropdown_cutout.png) 

[Centerboxes](/user/template/centerboxes/) are located below the page content as portrayed in the image below. 

## Centerbox Location & Sort Order

![Centerbox Location](/images/centerbox_location.png)
<br><br>

For example, when you don't want to show *New Products* anywhere in the cart, you turn off the link in the Categories sidebox and make sure the *New Products* sidebox is disabled. The *New Products* are still showing, however, on all the listed pages in the centerboxes below the page content as shown in the above image. Your next step then is to change the settings in the **Index Listing:** 

![Index Listing](/images/index_listing.png)

Most of the **Index Listing** settings control whether the different centerboxes show on different pages. Other settings at the bottom of the menu control the number of products showing per row in the centerboxes. 

The centerboxes are **New Products**, **Featured Products**, **Special Products** and **Upcoming** (or Expected) **Products**. There are four settings for each centerbox which correspond to the four locations where the centerboxes are displayed.


The *New*, *Featured* and *Special Products* all look the same: a row of products: 

![Featured Products Centerbox](/images/centerbox_featured.png)

The *Upcoming Products* looks very different:

![Upcoming Products Centerbox](/images/centerbox_upcoming.png)

## Page Locations

Those locations are **Main Page** (or the home page), **Category with Subcategories**, **Product listing**, and **Errors & Missing Products**. These are all turned on by default. The image above shows the home page with the lower portion of the centerboxes. The  **Category with Subcategories** url starts /index.php?main_page=index&cPath=. This then is any category or subcategory that has a subcategory. **Product Listing** is a category with no subcategories where the products are listed on the page. **Errors & Missing Products** obviously is when a category or product does not exist but a visitor puts in the wrong url.  

If you do not want a specific centerbox showing anywhere, change the number to zero on each of the four page locations. Anything besides zero designates the sort order of the boxes with the lowest number being displayed first. The default settings have *New Products* first and the others in this order: *Featured Products* (2), *Specials* (3) and *Upcoming* (4). 

## Number of Products per Row

The next set of settings towards the bottom of the menu are the *Per Row* choice: the number of products that appear per row. 

![Centerboxes per Category Row](/images/centerbox_per_row.png)

The numbers range up to 12 per row but as you can see by the image below, the actual number showing needs to be more about what looks right in the display as well as not exceeding the number of products available. This is *New Products* changed to 12 and there are only 9 products allowed by [*Configuration > Maximum Values*](/user/admin_pages/configuration/configuration_maximumvalues/) so those nine are compressed into 1/12 partitions, leaving white space (3 nonexistent products) to the right and crowding the other nine.

![Crowded Centerboxes](/images/centerbox_per_row_expanded.png)

Changing the number to 9, improves the display but can still be too crowded for most sites.

![Crowded Centerboxes 2](/images/centerbox_per_row_expanded2.png)

## Filtering Products for Categories

The last setting on the index menu is <em>Filter Product Listing for Current Top Level Category When Enabled</em>.

The centerboxes on the home page and the errors and missing pages will show all eligible products but that is not necessarily the case on the other pages.  If you are in a specific category with sub-categories, those boxes will display only products from those sub-categories. On the product listing page, all products within the parent category will show. That final setting, however, will change that to all products instead of just category-specific products by selecting 0 instead of the default 1. 

![Filter for Centerboxes](/images/centerbox_filter.png)

The Zen Cart demo data has nine featured products, but in the Hardware Category only two are featured. Both show on the first page where all eight sub-categories appear. But on the product listing page in the mice category, only the featured mouse appears.

Hardware Subcategories:

![Hardware Subcategories Featured Products](/images/centerbox_featured_hardware2.png)

Mouse Subcategory

![Mouse Subcategory Featured Product](/images/centerbox_featured_hardware.png)
<br><br>

**Note**: The centerboxes shown on the Shopping Cart page when it is empty are controlled in [Admin > Configuration > Stock](/user/admin_pages/configuration/configuration_stock/). 
