---
title: Display Product Listing Settings
description: Display settings for featured, new and all listings
category: template 
weight: 10
---

In admin there are a number of product display settings that are similar: the featured products, new and all products listings. As the configuration fields are identical, we can address all of these at once.

For example, Admin > Configuration > Featured Listing, the top settings are:

![Featured Products Settings](/images/featured_products_settings.png) 

Note that each setting has a four digit value; each digit or combination of digits controls a separate setting. 

The first digit controls whether that piece of the listing, say the product name, will show or not. You have to chose either a 1 or a 2 in order for it to show on the listing. Product name has a value of 2101, indicating it is to be shown. If that value was changed to 3101, it disappears from the page. 

The first digit also determines whether the item is located on the left or right as in the shot below where the 2101 was changed to 1101. One is for left and two is for right.

![Featured Change Name Number](/images/featured_product_settings2.png) 

The second and third digit taken together decides the sort order of the items in the display. For example, change the model number from 2101 to 2311, places it below the manufacturer name that has a number of 2302. 

![Featured Change Model Number](/images/featured_product_settings3.png) 

The fourth number decides the spacing between fields. If we just change the manufacturer number above from 2302 to 2301, the space between the manufacturer and model number disappears. Peeking under the hood, this setting controls how many line breaks are present, i.e, one, two or however many you may want. 

![Featured Change Manufacturer Spacing](/images/featured_product_settings4.png) 

