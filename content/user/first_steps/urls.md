---
title: Basics - URLs 
description: Zen Cart URL structure
category: first_steps
weight: 10
---

Some commonly referenced pages and their URLs are shown in this table:

Page | URL
-----|----
About Us | index.php?main_page=about_us
Advanced Search | main_page=advanced_search 
All Products | main_page=products_all 
Conditions of Use | index.php?main_page=conditions
Contact Us | index.php?main_page=contact_us
Featured Products| index.php?main_page=featured 
New Products | index.php?main_page=products_new
Privacy | index.php?main_page=privacy
Reviews | index.php?main_page=reviews
Shipping | index.php?main_page=shippinginfo
Specials | index.php?main_page=specials

<br><br>
 
Product and Category URLs have additional parameters.  The URL for product 27, which is in category 5 under category 1 would be 

```
index.php?main_page=product_info&cPath=1_5&products_id=27
```

or 

```
index.php?main_page=product_info&products_id=27
```

The URL for category 5 would be  

```
index.php?main_page=index&cPath=1_5
```

**Note:** If the setting [Skip 1-prod Categories]() is True, and there was only one product in category 5, this page would be skipped and the product info page would be shown directly.

