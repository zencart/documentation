---
title: Show Flags
description: Changing the behavior of your cart from the admin 
category: customizing
weight: 10
---

To allow users to modify the appearance of their cart without modifying core files (or indeed, any code file), a series of flags are provided in admin whose names begin with `SHOW_`.  

| configuration_key                                 | configuration_title                                                    | configuration_group_id |Admin Page|
|---|---|---|---|
| SHOW_COUNTS                                       | Show Category Counts                                                   |                      1 |Configuration > My Store
| SHOW_COUNTS_ADMIN                                 | Show Category Counts - Admin                                           |                      1 |
| SHOW_VERSION_UPDATE_IN_HEADER                     | Show if version update available                                       |                      1 |
| SHOW_CATEGORY_PRODUCTS_LINKED_STATUS              | Show linked status for categories                                      |                      1 |
| SHOW_SPLIT_TAX_CHECKOUT                           | Show Split Tax Lines                                                   |                      1 |
| SHOW_NEW_PRODUCTS_LIMIT                           | New Product Listing - Limited to ...                                   |                      3 | Configuration > Min Values 
| SHOW_CREATE_ACCOUNT_DEFAULT_COUNTRY               | Create Account Default Country ID                                      |                      5 |
| SHOW_SHIPPING_ESTIMATOR_BUTTON                    | Shipping Estimator Display Settings for Shopping Cart                  |                      7 | Configuration > Shipping 
| SHOW_PRODUCTS_SOLD_OUT                            | Products status in Catalog when out of stock should be set to          |                      9 | Configuration > Stock
| SHOW_SHOPPING_CART_EMPTY_FEATURED_PRODUCTS        | Show Featured Products on empty Shopping Cart Page                     |                      9 |
| SHOW_SHOPPING_CART_EMPTY_NEW_PRODUCTS             | Show New Products on empty Shopping Cart Page                          |                      9 |
| SHOW_SHOPPING_CART_COMBINED                       | Show Notice of Combining Shopping Cart on Login                        |                      9 |
| SHOW_SHOPPING_CART_DELETE                         | Show Shopping Cart - Delete Checkboxes or Delete Button                |                      9 |
| SHOW_SHOPPING_CART_UPDATE                         | Show Shopping Cart - Update Cart Button Location                       |                      9 |
| SHOW_PRODUCTS_SOLD_OUT_IMAGE                      | Show Sold Out Image in place of Add to Cart                            |                      9 |
| SHOW_SHOPPING_CART_EMPTY_SPECIALS_PRODUCTS        | Show Special Products on empty Shopping Cart Page                      |                      9 |
| SHOW_SHOPPING_CART_EMPTY_UPCOMING                 | Show Upcoming Products on empty Shopping Cart Page                     |                      9 |
| SHOW_NEWSLETTER_UNSUBSCRIBE_LINK                  | Display "Newsletter Unsubscribe" Link?                                 |                     12 | Configuration > Email 
| SHOW_ACCEPTED_CREDIT_CARDS                        | Credit Card Enabled - Show on Payment                                  |                     17 | Configuration > Credit Cards
| SHOW_PRODUCT_INFO_COLUMNS_ALSO_PURCHASED_PRODUCTS | Also Purchased Products Columns per Row                                |                     18 | Configuration > Product Info
| SHOW_PREVIOUS_NEXT_IMAGES                         | Previous Next - Button and Image Settings                              |                     18 |
| SHOW_PREVIOUS_NEXT_STATUS                         | Previous Next - Button and Image Status                                |                     18 |
| SHOW_SALE_DISCOUNT                                | Product Info - Show Sales Discount Savings Dollars or Percentage       |                     18 |
| SHOW_SALE_DISCOUNT_DECIMALS                       | Product Info - Show Sales Discount Savings Percentage Decimals         |                     18 |
| SHOW_SALE_DISCOUNT_STATUS                         | Product Info - Show Sales Discount Savings Status                      |                     18 |
| SHOW_BANNERS_GROUP_SET_ALL                        | Banner Display Group - Side Box banner_box_all                         |                     19 | Configuration > Layout Settings 
| SHOW_BANNERS_GROUP_SET4                           | Banner Display Groups - Footer Position 1                              |                     19 |
| SHOW_BANNERS_GROUP_SET5                           | Banner Display Groups - Footer Position 2                              |                     19 |
| SHOW_BANNERS_GROUP_SET6                           | Banner Display Groups - Footer Position 3                              |                     19 |
| SHOW_BANNERS_GROUP_SET1                           | Banner Display Groups - Header Position 1                              |                     19 |
| SHOW_BANNERS_GROUP_SET2                           | Banner Display Groups - Header Position 2                              |                     19 |
| SHOW_BANNERS_GROUP_SET3                           | Banner Display Groups - Header Position 3                              |                     19 |
| SHOW_BANNERS_GROUP_SET7                           | Banner Display Groups - Side Box banner_box                            |                     19 |
| SHOW_BANNERS_GROUP_SET8                           | Banner Display Groups - Side Box banner_box2                           |                     19 |
| SHOW_CATEGORIES_SUBCATEGORIES_ALWAYS              | Categories - Always Open to Show SubCategories                         |                     19 |
| SHOW_CATEGORIES_ALWAYS                            | Categories - Always Show on Main Page                                  |                     19 |
| SHOW_CATEGORIES_BOX_FEATURED_PRODUCTS             | Categories Box - Show Featured Products Link                           |                     19 |
| SHOW_CATEGORIES_BOX_PRODUCTS_ALL                  | Categories Box - Show Products All Link                                |                     19 |
| SHOW_CATEGORIES_BOX_PRODUCTS_NEW                  | Categories Box - Show Products New Link                                |                     19 |
| SHOW_CATEGORIES_BOX_SPECIALS                      | Categories Box - Show Specials Link                                    |                     19 |
| SHOW_CATEGORIES_SEPARATOR_LINK                    | Categories Separator between links Status                              |                     19 |
| SHOW_CUSTOMER_GREETING                            | Customer Greeting - Show on Index Page                                 |                     19 |
| SHOW_FOOTER_IP                                    | Footer - Show IP Address status                                        |                     19 |
| SHOW_TOTALS_IN_CART                               | Shopping Cart - Show Totals                                            |                     19 |
| SHOW_SHOPPING_CART_BOX_STATUS                     | Shopping Cart Box Status                                               |                     19 |
| SHOW_ACCOUNT_LINKS_ON_SITE_MAP                    | Site Map - include My Account Links?                                   |                     19 |
| SHOW_NEW_PRODUCTS_UPCOMING_MASKED                 | Mask Upcoming Products from being included as New Products             |                     21 | Configuration > New Listing
| SHOW_PRODUCT_INFO_COLUMNS_FEATURED_PRODUCTS       | Featured Products Columns per Row                                      |                     24 | Configuration > Index Listing
| SHOW_PRODUCT_INFO_ALL_PRODUCTS                    | Filter Product Listing for Current Top Level Category When Enabled     |                     24 |
| SHOW_PRODUCT_INFO_COLUMNS_NEW_PRODUCTS            | New Products Columns per Row                                           |                     24 |
| SHOW_PRODUCT_INFO_LISTING_BELOW_FEATURED_PRODUCTS | Show Featured Products - below Product Listing                         |                     24 |
| SHOW_PRODUCT_INFO_MAIN_FEATURED_PRODUCTS          | Show Featured Products on Main Page                                    |                     24 |
| SHOW_PRODUCT_INFO_CATEGORY_FEATURED_PRODUCTS      | Show Featured Products on Main Page - Category with SubCategories      |                     24 |
| SHOW_PRODUCT_INFO_MISSING_FEATURED_PRODUCTS       | Show Featured Products on Main Page - Errors and Missing Products Page |                     24 |
| SHOW_PRODUCT_INFO_LISTING_BELOW_NEW_PRODUCTS      | Show New Products - below Product Listing                              |                     24 |
| SHOW_PRODUCT_INFO_MAIN_NEW_PRODUCTS               | Show New Products on Main Page                                         |                     24 |
| SHOW_PRODUCT_INFO_CATEGORY_NEW_PRODUCTS           | Show New Products on Main Page - Category with SubCategories           |                     24 |
| SHOW_PRODUCT_INFO_MISSING_NEW_PRODUCTS            | Show New Products on Main Page - Errors and Missing Products Page      |                     24 |
| SHOW_PRODUCT_INFO_LISTING_BELOW_SPECIALS_PRODUCTS | Show Special Products - below Product Listing                          |                     24 |
| SHOW_PRODUCT_INFO_MAIN_SPECIALS_PRODUCTS          | Show Special Products on Main Page                                     |                     24 |
| SHOW_PRODUCT_INFO_CATEGORY_SPECIALS_PRODUCTS      | Show Special Products on Main Page - Category with SubCategories       |                     24 |
| SHOW_PRODUCT_INFO_MISSING_SPECIALS_PRODUCTS       | Show Special Products on Main Page - Errors and Missing Products Page  |                     24 |
| SHOW_PRODUCT_INFO_LISTING_BELOW_UPCOMING          | Show Upcoming Products - below Product Listing                         |                     24 |
| SHOW_PRODUCT_INFO_MAIN_UPCOMING                   | Show Upcoming Products on Main Page                                    |                     24 |
| SHOW_PRODUCT_INFO_CATEGORY_UPCOMING               | Show Upcoming Products on Main Page - Category with SubCategories      |                     24 |
| SHOW_PRODUCT_INFO_MISSING_UPCOMING                | Show Upcoming Products on Main Page - Errors and Missing Products Page |                     24 |
| SHOW_PRODUCT_INFO_COLUMNS_SPECIALS_PRODUCTS       | Special Products Columns per Row                                       |                     24 |
