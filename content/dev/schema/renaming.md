---
title: Renaming Database Table-Prefixes
category: schema 
description: How to Batch-Rename Database Tables
---

The use of [database prefixes](/user/first_steps/database/#what-are-prefixes) was common in the past but is not common or recommended now that hosting plans are more generous with the number of databases permitted. 

## Removing Database Table-Name Prefixes

If your database has tables named with a `zen_` or `zc_` or other prefix and you want to remove those prefixes, you must rename all those tables manually, and update your Zen Cart configuration to recognize the change.

1. Rename all the tables. See the script/instructions below.
2. Update your `/YOUR_ADMIN/includes/configure.php` and `/includes/configure.php` files by setting the `DB_PREFIX` to `''` instead of `'zen_'` or whatever it had before.
 (Remember that those configure.php files might be read-only, so make their permissions writable before attempting to save your changes.)
 

## Generating a Rename Script

The following short SQL statement can be run via phpMyAdmin to generate a complete script for renaming.

Be sure to replace THREE placeholders: 
- there are 2 mentions of `'zen_'` here, which should be replaced with whatever your CURRENT prefix is (see DB_PREFIX in your configure.php files).
- and `'PUT_DATABASE_NAME_HERE'` should contain the name of your Zen Cart database (see DB_DATABASE in your configure.php files).

```
SELECT CONCAT ('RENAME TABLE ', table_name, ' TO ', REPLACE(table_name, 'zen_', ''),';')
FROM information_schema.tables
WHERE table_name LIKE 'zen_%'
  AND table_schema='PUT_DATABASE_NAME_HERE'
```

After you run the script, it will generate output like the following. Copy-and-paste all those "rename" statements to run them.
Be sure to update your configure.php files as mentioned above.

### Sample output for renaming tables
```
RENAME TABLE zen_address_book TO address_book;
RENAME TABLE zen_address_format TO address_format;
RENAME TABLE zen_admin TO admin;
RENAME TABLE zen_admin_activity_log TO admin_activity_log;
RENAME TABLE zen_admin_menus TO admin_menus;
RENAME TABLE zen_admin_notifications TO admin_notifications;
RENAME TABLE zen_admin_pages TO admin_pages;
RENAME TABLE zen_admin_pages_to_profiles TO admin_pages_to_profiles;
RENAME TABLE zen_admin_profiles TO admin_profiles;
RENAME TABLE zen_authorizenet TO authorizenet;
RENAME TABLE zen_banners TO banners;
RENAME TABLE zen_banners_history TO banners_history;
RENAME TABLE zen_categories TO categories;
RENAME TABLE zen_categories_description TO categories_description;
RENAME TABLE zen_configuration TO configuration;
RENAME TABLE zen_configuration_group TO configuration_group;
RENAME TABLE zen_counter TO counter;
RENAME TABLE zen_counter_history TO counter_history;
RENAME TABLE zen_countries TO countries;
RENAME TABLE zen_coupon_email_track TO coupon_email_track;
RENAME TABLE zen_coupon_gv_customer TO coupon_gv_customer;
RENAME TABLE zen_coupon_gv_queue TO coupon_gv_queue;
RENAME TABLE zen_coupon_redeem_track TO coupon_redeem_track;
RENAME TABLE zen_coupon_restrict TO coupon_restrict;
RENAME TABLE zen_coupons TO coupons;
RENAME TABLE zen_coupons_description TO coupons_description;
RENAME TABLE zen_currencies TO currencies;
RENAME TABLE zen_customers TO customers;
RENAME TABLE zen_customers_basket TO customers_basket;
RENAME TABLE zen_customers_basket_attributes TO customers_basket_attributes;
RENAME TABLE zen_customers_info TO customers_info;
RENAME TABLE zen_db_cache TO db_cache;
RENAME TABLE zen_email_archive TO email_archive;
RENAME TABLE zen_ezpages TO ezpages;
RENAME TABLE zen_ezpages_content TO ezpages_content;
RENAME TABLE zen_featured TO featured;
RENAME TABLE zen_files_uploaded TO files_uploaded;
RENAME TABLE zen_geo_zones TO geo_zones;
RENAME TABLE zen_get_terms_to_filter TO get_terms_to_filter;
RENAME TABLE zen_group_pricing TO group_pricing;
RENAME TABLE zen_languages TO languages;
RENAME TABLE zen_layout_boxes TO layout_boxes;
RENAME TABLE zen_manufacturers TO manufacturers;
RENAME TABLE zen_manufacturers_info TO manufacturers_info;
RENAME TABLE zen_media_clips TO media_clips;
RENAME TABLE zen_media_manager TO media_manager;
RENAME TABLE zen_media_to_products TO media_to_products;
RENAME TABLE zen_media_types TO media_types;
RENAME TABLE zen_meta_tags_categories_description TO meta_tags_categories_description;
RENAME TABLE zen_meta_tags_products_description TO meta_tags_products_description;
RENAME TABLE zen_music_genre TO music_genre;
RENAME TABLE zen_newsletters TO newsletters;
RENAME TABLE zen_orders TO orders;
RENAME TABLE zen_orders_products TO orders_products;
RENAME TABLE zen_orders_products_attributes TO orders_products_attributes;
RENAME TABLE zen_orders_products_download TO orders_products_download;
RENAME TABLE zen_orders_status TO orders_status;
RENAME TABLE zen_orders_status_history TO orders_status_history;
RENAME TABLE zen_orders_total TO orders_total;
RENAME TABLE zen_paypal TO paypal;
RENAME TABLE zen_paypal_payment_status TO paypal_payment_status;
RENAME TABLE zen_paypal_payment_status_history TO paypal_payment_status_history;
RENAME TABLE zen_paypal_session TO paypal_session;
RENAME TABLE zen_paypal_testing TO paypal_testing;
RENAME TABLE zen_product_music_extra TO product_music_extra;
RENAME TABLE zen_product_type_layout TO product_type_layout;
RENAME TABLE zen_product_types TO product_types;
RENAME TABLE zen_product_types_to_category TO product_types_to_category;
RENAME TABLE zen_products TO products;
RENAME TABLE zen_products_attributes TO products_attributes;
RENAME TABLE zen_products_attributes_download TO products_attributes_download;
RENAME TABLE zen_products_description TO products_description;
RENAME TABLE zen_products_discount_quantity TO products_discount_quantity;
RENAME TABLE zen_products_notifications TO products_notifications;
RENAME TABLE zen_products_options TO products_options;
RENAME TABLE zen_products_options_types TO products_options_types;
RENAME TABLE zen_products_options_values TO products_options_values;
RENAME TABLE zen_products_options_values_to_products_options TO products_options_values_to_products_options;
RENAME TABLE zen_products_to_categories TO products_to_categories;
RENAME TABLE zen_project_version TO project_version;
RENAME TABLE zen_project_version_history TO project_version_history;
RENAME TABLE zen_query_builder TO query_builder;
RENAME TABLE zen_record_artists TO record_artists;
RENAME TABLE zen_record_artists_info TO record_artists_info;
RENAME TABLE zen_record_company TO record_company;
RENAME TABLE zen_record_company_info TO record_company_info;
RENAME TABLE zen_reviews TO reviews;
RENAME TABLE zen_reviews_description TO reviews_description;
RENAME TABLE zen_salemaker_sales TO salemaker_sales;
RENAME TABLE zen_sessions TO sessions;
RENAME TABLE zen_specials TO specials;
RENAME TABLE zen_tax_class TO tax_class;
RENAME TABLE zen_tax_rates TO tax_rates;
RENAME TABLE zen_template_select TO template_select;
RENAME TABLE zen_upgrade_exceptions TO upgrade_exceptions;
RENAME TABLE zen_whos_online TO whos_online;
RENAME TABLE zen_zones TO zones;
RENAME TABLE zen_zones_to_geo_zones TO zones_to_geo_zones;
```
