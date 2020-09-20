---
title: Basics - URLs 
description: URL structure used by Zen Cart 
category: first_steps
weight: 10
---

Some commonly referenced pages and their URLs are shown in this table:

Page | URL
-----|----
About Us | index.php?main_page=about_us
Advanced Search | index.php?main_page=advanced_search 
All Products | index.php?main_page=products_all 
Conditions of Use | index.php?main_page=conditions
Contact Us | index.php?main_page=contact_us
Featured Products| index.php?main_page=featured 
New Products | index.php?main_page=products_new
Privacy | index.php?main_page=privacy
Reviews | index.php?main_page=reviews
Shipping | index.php?main_page=shippinginfo
Shopping Cart | index.php?main_page=shopping_cart 
Specials | index.php?main_page=specials

<br><br>

Some pages cannot be accessed unless a visitor is logged in.
These are the pages in the checkout flow. 

<br><br>

Page | URL
-----|----
Checkout Shipping | index.php?main_page=checkout_shipping 
Checkout Payment | index.php?main_page=checkout_payment
Checkout Confirmation| index.php?main_page=checkout_confirmation 
Checkout Success | index.php?main_page=checkout_success 

Other pages which cannot be accessed unless a customer is logged in pertain to 
account management: 

Page | URL
-----|----
Account | index.php?main_page=account
Account Edit | index.php?main_page=account_edit
Account History | index.php?main_page=account_history 
 
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

**Note:** If the setting [Skip 1-prod Categories](/user/admin_pages/configuration/configuration_layoutsettings/#skip_1prod_categories) is True, and there was only one product in category 5, this page would be skipped and the product info page would be shown directly.

For a more complete list of pages, see [storefront pages - complete list](/user/storefront_pages/complete_list/).
