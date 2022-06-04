---
title: Storefront Pages - A Complete List
description: All the pages in your storefront
category: storefront_pages 
weight: 10
---

Pages not requiring login are: 

Page | URL | Notes 
-----|-----|------
About Us | index.php?main_page=about_us | 
Advanced Search | index.php?main_page=advanced_search  | 
Advanced Search Result | index.php?main_page=advanced_search_result  | 
All Products | index.php?main_page=products_all  | 
Brands | index.php?main_page=brands | Shop by Brand
Category Listing |  index.php?main_page=index&cPath=NNN | Shows subcategories in a category
Conditions of Use | index.php?main_page=conditions | 
Contact Us | index.php?main_page=contact_us | 
Create Account | index.php?main_page=create_account | 
Create Account Success | index.php?main_page=create_account_success | 
Discount Coupon | index.php?main_page=discount_coupon | 
Featured Products| index.php?main_page=featured  | 
New Products | index.php?main_page=products_new | 
Page | index.php?main_page=page | Displays an EZ-Page 
Page 2 | index.php?main_page=page_2 | 
Page 3 | index.php?main_page=page_3 | 
Page 4 | index.php?main_page=page_4 | 
Privacy | index.php?main_page=privacy | Privacy Policy
Product Listing |  index.php?main_page=index&cPath=NNN | Shows products in a category 
Product Reviews Info | index.php?main_page=product_reviews_info | Read a specific review 
Reviews | index.php?main_page=reviews | Read all reviews 
Shipping | index.php?main_page=shippinginfo | Shipping Policy
Site Map | index.php?main_page=site_map | 
Shopping Cart | index.php?main_page=shopping_cart | 
Specials | index.php?main_page=specials | 

<br><br>

Some pages cannot be accessed unless a visitor is logged in: 

<br><br>

Page | URL | Notes 
-----|-----|------
Account | index.php?main_page=account | 
Account Edit | index.php?main_page=account_edit | 
Account History | index.php?main_page=account_history  | View all orders 
Account History Info | index.php?main_page=account_history_info  | View a single order 
Account Newsletters | index.php?main_page=account_newsletters | Manage newsletter subscription
Account Notifications | index.php?main_page=account_notifications | 
Account Password | index.php?main_page=account_password | 
Address Book | index.php?main_page=address_book | 
Ask a Question | index.php?main_page=ask_a_question | 
Checkout Confirmation| index.php?main_page=checkout_confirmation  | 
Checkout Payment | index.php?main_page=checkout_payment | 
Checkout Payment Address | index.php?main_page=checkout_payment_address | 
Checkout Shipping Address | index.php?main_page=checkout_shipping_address  | 
Checkout Shipping | index.php?main_page=checkout_shipping  | 
Checkout Success | index.php?main_page=checkout_success  | 
Product Reviews Write | index.php?main_page=product_reviews_write | Write a review 
Unsubscribe | index.php?main_page=unsubscribe | Unsubscribe from Newsletter
 
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

