---
title: Zen Cart 1.3.9 Schema 
category: schema 
weight: -139
---

[address_book](#address_book)    [address_format](#address_format)    [admin](#admin)    [admin_activity_log](#admin_activity_log)    [authorizenet](#authorizenet)    [banners](#banners)    [banners_history](#banners_history)    [categories](#categories)    [categories_description](#categories_description)    [configuration](#configuration)    [configuration_group](#configuration_group)    [counter](#counter)    [counter_history](#counter_history)    [countries](#countries)    [coupon_email_track](#coupon_email_track)    [coupon_gv_customer](#coupon_gv_customer)    [coupon_gv_queue](#coupon_gv_queue)    [coupon_redeem_track](#coupon_redeem_track)    [coupon_restrict](#coupon_restrict)    [coupons](#coupons)    [coupons_description](#coupons_description)    [currencies](#currencies)    [customers](#customers)    [customers_basket](#customers_basket)    [customers_basket_attributes](#customers_basket_attributes)    [customers_info](#customers_info)    [customers_wishlist](#customers_wishlist)    [db_cache](#db_cache)    [email_archive](#email_archive)    [ezpages](#ezpages)    [featured](#featured)    [files_uploaded](#files_uploaded)    [geo_zones](#geo_zones)    [get_terms_to_filter](#get_terms_to_filter)    [group_pricing](#group_pricing)    [languages](#languages)    [layout_boxes](#layout_boxes)    [manufacturers](#manufacturers)    [manufacturers_info](#manufacturers_info)    [media_clips](#media_clips)    [media_manager](#media_manager)    [media_to_products](#media_to_products)    [media_types](#media_types)    [meta_tags_categories_description](#meta_tags_categories_description)    [meta_tags_products_description](#meta_tags_products_description)    [music_genre](#music_genre)    [newsletters](#newsletters)    [orders](#orders)    [orders_products](#orders_products)    [orders_products_attributes](#orders_products_attributes)    [orders_products_download](#orders_products_download)    [orders_status](#orders_status)    [orders_status_history](#orders_status_history)    [orders_total](#orders_total)    [paypal](#paypal)    [paypal_payment_status](#paypal_payment_status)    [paypal_payment_status_history](#paypal_payment_status_history)    [paypal_session](#paypal_session)    [paypal_testing](#paypal_testing)    [product_music_extra](#product_music_extra)    [product_type_layout](#product_type_layout)    [product_types](#product_types)    [product_types_to_category](#product_types_to_category)    [products](#products)    [products_attributes](#products_attributes)    [products_attributes_download](#products_attributes_download)    [products_description](#products_description)    [products_discount_quantity](#products_discount_quantity)    [products_notifications](#products_notifications)    [products_options](#products_options)    [products_options_types](#products_options_types)    [products_options_values](#products_options_values)    [products_options_values_to_products_options](#products_options_values_to_products_options)    [products_to_categories](#products_to_categories)    [project_version](#project_version)    [project_version_history](#project_version_history)    [query_builder](#query_builder)    [record_artists](#record_artists)    [record_artists_info](#record_artists_info)    [record_company](#record_company)    [record_company_info](#record_company_info)    [reviews](#reviews)    [reviews_description](#reviews_description)    [salemaker_sales](#salemaker_sales)    [sessions](#sessions)    [specials](#specials)    [tax_class](#tax_class)    [tax_rates](#tax_rates)    [template_select](#template_select)    [upgrade_exceptions](#upgrade_exceptions)    [whos_online](#whos_online)    [zones](#zones)    [zones_to_geo_zones](#zones_to_geo_zones) 


<hr />

Legend: **bolded fields** are primary keys, [links](#) are foreign keys.  

<hr />

## address_book

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**address_book_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_gender</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_company</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_firstname</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_lastname</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_street_address</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_suburb</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_postcode</td>

<td class="db_td">varchar(10)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_city</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_state</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_country_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_zone_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## address_book

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**address_book_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_gender</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_company</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_firstname</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_lastname</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_street_address</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_suburb</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_postcode</td>

<td class="db_td">varchar(10)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_city</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_state</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_country_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">entry_zone_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## address_format

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**address_format_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_format</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_summary</td>

<td class="db_td">varchar(48)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## admin

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**admin_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">admin_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">admin_email</td>

<td class="db_td">varchar(96)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">admin_pass</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">admin_level</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## admin_activity_log

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**log_id**

</td>

<td class="db_td">int(15)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">access_date</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[admin_id](#admin)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">page_accessed</td>

<td class="db_td">varchar(80)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">page_parameters</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">ip_address</td>

<td class="db_td">varchar(15)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## authorizenet

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**id**

</td>

<td class="db_td">int(11) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customer_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[order_id](#orders)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">response_code</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">response_text</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">authorization_type</td>

<td class="db_td">varchar(50)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">transaction_id</td>

<td class="db_td">bigint(20)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sent</td>

<td class="db_td">longtext</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">received</td>

<td class="db_td">longtext</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">time</td>

<td class="db_td">varchar(50)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">session_id</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## banners

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**banners_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_title</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_url</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_image</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_group</td>

<td class="db_td">varchar(15)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_html_text</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">expires_impressions</td>

<td class="db_td">int(7)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">expires_date</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_scheduled</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_status_change</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">status</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_open_new_windows</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_on_ssl</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_sort_order</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## banners_history

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**banners_history_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[banners_id](#banners)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_shown</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_clicked</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">banners_history_date</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## categories

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**categories_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">categories_image</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">parent_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sort_order</td>

<td class="db_td">int(3)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">categories_status</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## categories_description

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**categories_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[language_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">categories_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">categories_description</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## configuration

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**configuration_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_title</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_key</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">UNI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_value</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_description</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_group_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sort_order</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">use_function</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">set_function</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## configuration_group

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**configuration_group_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_group_title</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_group_description</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sort_order</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">visible</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## counter

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td class="db_td">startdate</td>

<td class="db_td">char(8)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">counter</td>

<td class="db_td">int(12)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## counter_history

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**startdate**

</td>

<td class="db_td">char(8)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">counter</td>

<td class="db_td">int(12)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">session_counter</td>

<td class="db_td">int(12)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## countries

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**countries_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">countries_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">countries_iso_code_2</td>

<td class="db_td">char(2)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">countries_iso_code_3</td>

<td class="db_td">char(3)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_format_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## coupon_email_track

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**unique_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[coupon_id](#coupons)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customer_id_sent</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sent_firstname</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sent_lastname</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">emailed_to</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_sent</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## coupon_gv_customer

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**customer_id**

</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">amount</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## coupon_gv_queue

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**unique_id**

</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customer_id](#customers)</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[order_id](#orders)</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">amount</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_created</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">ipaddr</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">release_flag</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">N</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## coupon_redeem_track

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**unique_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[coupon_id](#coupons)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customer_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">redeem_date</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">redeem_ip</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[order_id](#orders)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## coupon_restrict

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**restrict_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[coupon_id](#coupons)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[product_id](#products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[category_id](#categories)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_restrict</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">N</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## coupons

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**coupon_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_type</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">F</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_code</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_amount</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_minimum_order</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_start_date</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_expire_date</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">uses_per_coupon</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">uses_per_user</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">restrict_to_products</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">restrict_to_categories</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">restrict_to_customers</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_active</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">Y</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_created</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_zone_restriction</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## coupons_description

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**coupon_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[language_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_description</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## currencies

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**currencies_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">title</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">code</td>

<td class="db_td">char(3)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">symbol_left</td>

<td class="db_td">varchar(24)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">symbol_right</td>

<td class="db_td">varchar(24)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">decimal_point</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">thousands_point</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">decimal_places</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">value</td>

<td class="db_td">float(13,8)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_updated</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## customers

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**customers_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_gender</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_firstname</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_lastname</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_dob</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_email_address</td>

<td class="db_td">varchar(96)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_nick</td>

<td class="db_td">varchar(96)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_default_address_id](#address_book)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_telephone</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_fax</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_password</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_newsletter</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_group_pricing](#group_pricing)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_email_format</td>

<td class="db_td">varchar(4)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">TEXT</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_authorization</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_referral</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_paypal_payerid</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_paypal_ec</td>

<td class="db_td">tinyint(1) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## customers_basket

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**customers_basket_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_id](#products)</td>

<td class="db_td">tinytext</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_basket_quantity</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">final_price</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_basket_date_added</td>

<td class="db_td">varchar(8)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## customers_basket_attributes

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**customers_basket_attributes_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_id](#products)</td>

<td class="db_td">tinytext</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_options_id](#products_options)</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_options_value_id](#products_options_values)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_value_text</td>

<td class="db_td">blob</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_sort_order</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## customers_info

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**customers_info_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_info_date_of_last_logon</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_info_number_of_logons</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_info_date_account_created</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_info_date_account_last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">global_product_notifications</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## customers_wishlist

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td class="db_td">products_id</td>

<td class="db_td">int(13)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_id](#customers)</td>

<td class="db_td">int(13)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_model</td>

<td class="db_td">varchar(13)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_price</td>

<td class="db_td">decimal(8,2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">final_price</td>

<td class="db_td">decimal(8,2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_quantity</td>

<td class="db_td">int(2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">wishlist_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## db_cache

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**cache_entry_name**

</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">cache_data</td>

<td class="db_td">mediumblob</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">cache_entry_created</td>

<td class="db_td">int(15)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## email_archive

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**archive_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">email_to_name</td>

<td class="db_td">varchar(96)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">email_to_address</td>

<td class="db_td">varchar(96)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">email_from_name</td>

<td class="db_td">varchar(96)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">email_from_address</td>

<td class="db_td">varchar(96)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">email_subject</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">email_html</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">email_text</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_sent</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">module</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## ezpages

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**pages_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[languages_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">pages_title</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">alt_url</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">alt_url_external</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">pages_html_text</td>

<td class="db_td">mediumtext</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">status_header</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">status_sidebox</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">status_footer</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">status_toc</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">header_sort_order</td>

<td class="db_td">int(3)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sidebox_sort_order</td>

<td class="db_td">int(3)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">footer_sort_order</td>

<td class="db_td">int(3)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">toc_sort_order</td>

<td class="db_td">int(3)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">page_open_new_window</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">page_is_ssl</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">toc_chapter</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## featured

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**featured_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_id](#products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">featured_date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">featured_last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">expires_date</td>

<td class="db_td">date</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0001-01-01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_status_change</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">status</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">featured_date_available</td>

<td class="db_td">date</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0001-01-01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## files_uploaded

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**files_uploaded_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sesskey</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">files_uploaded_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## geo_zones

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**geo_zone_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">geo_zone_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">geo_zone_description</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## get_terms_to_filter

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**get_term_name**

</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">get_term_table</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">get_term_name_field</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## group_pricing

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**group_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">group_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">group_percentage</td>

<td class="db_td">decimal(5,2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## languages

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**languages_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">code</td>

<td class="db_td">char(2)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">image</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">directory</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sort_order</td>

<td class="db_td">int(3)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## layout_boxes

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**layout_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">layout_template</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">layout_box_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">layout_box_status</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">layout_box_location</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">layout_box_sort_order</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">layout_box_sort_order_single</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">layout_box_status_single</td>

<td class="db_td">tinyint(4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## manufacturers

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**manufacturers_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">manufacturers_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">manufacturers_image</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## manufacturers_info

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**manufacturers_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[languages_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">manufacturers_url</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">url_clicked</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_last_click</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## media_clips

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**clip_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">media_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">clip_type</td>

<td class="db_td">smallint(6)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">clip_filename</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## media_manager

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**media_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">media_name</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## media_to_products

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td class="db_td">media_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[product_id](#products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## media_types

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**type_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">type_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">type_ext</td>

<td class="db_td">varchar(8)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## meta_tags_categories_description

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**categories_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[language_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_title</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_keywords</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_description</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## meta_tags_products_description

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[language_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_title</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_keywords</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_description</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## music_genre

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**music_genre_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">music_genre_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## newsletters

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**newsletters_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">title</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">content</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">content_html</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">module</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_sent</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">status</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">locked</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## orders

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**orders_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_company</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_street_address</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_suburb</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_city</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_postcode</td>

<td class="db_td">varchar(10)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_state</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_country</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_telephone</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_email_address</td>

<td class="db_td">varchar(96)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_address_format_id</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">delivery_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">delivery_company</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">delivery_street_address</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">delivery_suburb</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">delivery_city</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">delivery_postcode</td>

<td class="db_td">varchar(10)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">delivery_state</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">delivery_country</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">delivery_address_format_id</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">billing_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">billing_company</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">billing_street_address</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">billing_suburb</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">billing_city</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">billing_postcode</td>

<td class="db_td">varchar(10)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">billing_state</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">billing_country</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">billing_address_format_id</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_method</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_module_code</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">shipping_method</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">shipping_module_code</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">coupon_code</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">cc_type</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">cc_owner</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">cc_number</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">cc_expires</td>

<td class="db_td">varchar(4)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">cc_cvv</td>

<td class="db_td">blob</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_purchased</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">orders_status</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">orders_date_finished</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">currency</td>

<td class="db_td">char(3)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">currency_value</td>

<td class="db_td">decimal(14,6)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">order_total</td>

<td class="db_td">decimal(14,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">order_tax</td>

<td class="db_td">decimal(14,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">paypal_ipn_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">ip_address</td>

<td class="db_td">varchar(96)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## orders_products

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**orders_products_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[orders_id](#orders)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_id](#products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_model</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_price</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">final_price</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_tax</td>

<td class="db_td">decimal(7,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_quantity</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">onetime_charges</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_priced_by_attribute</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">product_is_free</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_discount_type</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_discount_type_from</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_prid](#products)</td>

<td class="db_td">tinytext</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## orders_products_attributes

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**orders_products_attributes_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[orders_id](#orders)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[orders_products_id](#orders_products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_values</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">options_values_price</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">price_prefix</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">product_attribute_is_free</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_attributes_weight</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_attributes_weight_prefix</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_discounted</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_base_included</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_onetime</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_factor</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_factor_offset</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_factor_onetime</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_factor_onetime_offset</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_qty_prices</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_qty_prices_onetime</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_words</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_words_free</td>

<td class="db_td">int(4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_letters</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_letters_free</td>

<td class="db_td">int(4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_options_id](#products_options)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_values_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_prid](#products)</td>

<td class="db_td">tinytext</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## orders_products_download

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**orders_products_download_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[orders_id](#orders)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[orders_products_id](#orders_products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">orders_products_filename</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">download_maxdays</td>

<td class="db_td">int(2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">download_count</td>

<td class="db_td">int(2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_prid](#products)</td>

<td class="db_td">tinytext</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## orders_status

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**orders_status_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[language_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">orders_status_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## orders_status_history

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**orders_status_history_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[orders_id](#orders)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[orders_status_id](#orders_status)</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customer_notified</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">comments</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## orders_total

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**orders_total_id**

</td>

<td class="db_td">int(10) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[orders_id](#orders)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">title</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">text</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">value</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">class</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sort_order</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## paypal

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**paypal_ipn_id**

</td>

<td class="db_td">int(11) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[order_id](#orders)</td>

<td class="db_td">int(11) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">txn_type</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">module_name</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">module_mode</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">reason_code</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_type</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_status</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">pending_reason</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">invoice</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">mc_currency</td>

<td class="db_td">char(3)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">first_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payer_business_name</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_street</td>

<td class="db_td">varchar(254)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_city</td>

<td class="db_td">varchar(120)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_state</td>

<td class="db_td">varchar(120)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_zip</td>

<td class="db_td">varchar(10)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_country</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_status</td>

<td class="db_td">varchar(11)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payer_email</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payer_id</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payer_status</td>

<td class="db_td">varchar(10)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_date</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">business</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">receiver_email</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">receiver_id</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">txn_id</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">parent_txn_id</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">num_cart_items</td>

<td class="db_td">tinyint(4) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">mc_gross</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">mc_fee</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_gross</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_fee</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">settle_amount</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">settle_currency</td>

<td class="db_td">char(3)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">exchange_rate</td>

<td class="db_td">decimal(4,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">notify_version</td>

<td class="db_td">varchar(6)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">verify_sign</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">memo</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## paypal_payment_status

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**payment_status_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_status_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## paypal_payment_status_history

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**payment_status_history_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">paypal_ipn_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">txn_id</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">parent_txn_id</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_status</td>

<td class="db_td">varchar(17)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">pending_reason</td>

<td class="db_td">varchar(14)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## paypal_session

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**unique_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">session_id</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">saved_session</td>

<td class="db_td">mediumblob</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">expiry</td>

<td class="db_td">int(17)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## paypal_testing

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**paypal_ipn_id**

</td>

<td class="db_td">int(11) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[order_id](#orders)</td>

<td class="db_td">int(11) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">custom</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">txn_type</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">module_name</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">module_mode</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">reason_code</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_type</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_status</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">pending_reason</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">invoice</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">mc_currency</td>

<td class="db_td">char(3)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">first_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payer_business_name</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_street</td>

<td class="db_td">varchar(254)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_city</td>

<td class="db_td">varchar(120)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_state</td>

<td class="db_td">varchar(120)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_zip</td>

<td class="db_td">varchar(10)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_country</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">address_status</td>

<td class="db_td">varchar(11)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payer_email</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payer_id</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payer_status</td>

<td class="db_td">varchar(10)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_date</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">business</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">receiver_email</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">receiver_id</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">txn_id</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">parent_txn_id</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">num_cart_items</td>

<td class="db_td">tinyint(4) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">mc_gross</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">mc_fee</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_gross</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">payment_fee</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">settle_amount</td>

<td class="db_td">decimal(7,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">settle_currency</td>

<td class="db_td">char(3)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">exchange_rate</td>

<td class="db_td">decimal(4,2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">notify_version</td>

<td class="db_td">decimal(2,1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">verify_sign</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">memo</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## product_music_extra

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[artists_id](#record_artists)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">record_company_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">music_genre_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## product_type_layout

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**configuration_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_title</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_key</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">UNI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_value</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">configuration_description</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">product_type_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sort_order</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">use_function</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">set_function</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## product_types

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**type_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">type_name</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">type_handler</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">type_master_type</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">allow_add_to_cart</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">Y</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">default_image</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## product_types_to_category

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td class="db_td">product_type_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[category_id](#categories)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_type</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_quantity</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_model</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_image</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_price</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_virtual</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_date_available</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_weight</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_status</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_tax_class_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">manufacturers_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_ordered</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_quantity_order_min</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_quantity_order_units</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_priced_by_attribute</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">product_is_free</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">product_is_call</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_quantity_mixed</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">product_is_always_free_shipping</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_qty_box_status</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_quantity_order_max</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_sort_order</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_discount_type</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_discount_type_from</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_price_sorter</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[master_categories_id](#categories)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_mixed_discount_quantity</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_title_status</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_products_name_status</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_model_status</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_price_status</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">metatags_title_tagline_status</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_attributes

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_attributes_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_id](#products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[options_id](#products_options)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[options_values_id](#products_options_values)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">options_values_price</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">price_prefix</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_sort_order</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">product_attribute_is_free</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_attributes_weight</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_attributes_weight_prefix</td>

<td class="db_td">char(1)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_display_only</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_default</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_discounted</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_image</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_base_included</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_onetime</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_factor</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_factor_offset</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_factor_onetime</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_factor_onetime_offset</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_qty_prices</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_qty_prices_onetime</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_words</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_words_free</td>

<td class="db_td">int(4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_letters</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_price_letters_free</td>

<td class="db_td">int(4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">attributes_required</td>

<td class="db_td">tinyint(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_attributes_download

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_attributes_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_attributes_filename</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_attributes_maxdays</td>

<td class="db_td">int(2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_attributes_maxcount</td>

<td class="db_td">int(2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_description

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[language_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_description</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_url</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_viewed</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_discount_quantity

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td class="db_td">discount_id</td>

<td class="db_td">int(4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_id](#products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">discount_qty</td>

<td class="db_td">float</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">discount_price</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_notifications

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_options

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_options_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[language_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_sort_order</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_type</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_length</td>

<td class="db_td">smallint(2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">32</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_comment</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_size</td>

<td class="db_td">smallint(2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">32</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_images_per_row</td>

<td class="db_td">int(2)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">5</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_images_style</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_rows</td>

<td class="db_td">smallint(2)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_options_types

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_options_types_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_types_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_options_values

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_options_values_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[language_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_values_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_values_sort_order</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_options_values_to_products_options

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_options_values_to_products_options_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_options_id](#products_options)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">products_options_values_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## products_to_categories

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**products_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[categories_id](#categories)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## project_version

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**project_version_id**

</td>

<td class="db_td">tinyint(3)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_key</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">UNI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_major</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_minor</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_patch1</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_patch2</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_patch1_source</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_patch2_source</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_comment</td>

<td class="db_td">varchar(250)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_date_applied</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 01:01:01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## project_version_history

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**project_version_id**

</td>

<td class="db_td">tinyint(3)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_key</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_major</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_minor</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_patch</td>

<td class="db_td">varchar(20)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_comment</td>

<td class="db_td">varchar(250)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">project_version_date_applied</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 01:01:01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## query_builder

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**query_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">query_category</td>

<td class="db_td">varchar(40)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">query_name</td>

<td class="db_td">varchar(80)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">UNI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">query_description</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">query_string</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">query_keys_list</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## record_artists

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**artists_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">artists_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">artists_image</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## record_artists_info

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**artists_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[languages_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">artists_url</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">url_clicked</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_last_click</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## record_company

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**record_company_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">record_company_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">record_company_image</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## record_company_info

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**record_company_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[languages_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">record_company_url</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">url_clicked</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_last_click</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## reviews

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**reviews_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_id](#products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[customers_id](#customers)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">customers_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">reviews_rating</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">reviews_read</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">status</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## reviews_description

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**reviews_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[languages_id](#languages)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">reviews_text</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## salemaker_sales

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**sale_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_status</td>

<td class="db_td">tinyint(4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_name</td>

<td class="db_td">varchar(30)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_deduction_value</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_deduction_type</td>

<td class="db_td">tinyint(4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_pricerange_from</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_pricerange_to</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_specials_condition</td>

<td class="db_td">tinyint(4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_categories_selected</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_categories_all</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_date_start</td>

<td class="db_td">date</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0001-01-01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_date_end</td>

<td class="db_td">date</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0001-01-01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_date_added</td>

<td class="db_td">date</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_date_last_modified</td>

<td class="db_td">date</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sale_date_status_change</td>

<td class="db_td">date</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## sessions

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**sesskey**

</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">expiry</td>

<td class="db_td">int(11) unsigned</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">value</td>

<td class="db_td">mediumblob</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## specials

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**specials_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[products_id](#products)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">specials_new_products_price</td>

<td class="db_td">decimal(15,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">specials_date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">specials_last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">expires_date</td>

<td class="db_td">date</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0001-01-01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_status_change</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">status</td>

<td class="db_td">int(1)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">specials_date_available</td>

<td class="db_td">date</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0001-01-01</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## tax_class

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**tax_class_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">tax_class_title</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">tax_class_description</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## tax_rates

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**tax_rates_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">tax_zone_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[tax_class_id](#tax_class)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">tax_priority</td>

<td class="db_td">int(5)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">1</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">tax_rate</td>

<td class="db_td">decimal(7,4)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0.0000</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">tax_description</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## template_select

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**template_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">template_dir</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">template_language</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## upgrade_exceptions

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**upgrade_exception_id**

</td>

<td class="db_td">smallint(5)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sql_file</td>

<td class="db_td">varchar(50)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">reason</td>

<td class="db_td">varchar(200)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">errordate</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">sqlstatement</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## whos_online

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td class="db_td">customer_id</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">full_name</td>

<td class="db_td">varchar(64)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">session_id</td>

<td class="db_td">varchar(128)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">ip_address</td>

<td class="db_td">varchar(15)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">time_entry</td>

<td class="db_td">varchar(14)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">time_last_click</td>

<td class="db_td">varchar(14)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_page_url</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">host_address</td>

<td class="db_td">text</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">user_agent</td>

<td class="db_td">varchar(255)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## zones

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**zone_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[zone_country_id](#countries)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">zone_code</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">zone_name</td>

<td class="db_td">varchar(32)</td>

<td class="db_td">latin1_general_ci</td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

## zones_to_geo_zones

<table class="db_table">

<tbody>

<tr>

<td>Field</td>

<td>Type</td>

<td>Collation</td>

<td>Null</td>

<td>Key</td>

<td>Default</td>

<td>Extra</td>

<td>Comment</td>

</tr>

<tr class="db_tr">

<td>

**association_id**

</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td">PRI</td>

<td class="db_td"></td>

<td class="db_td">auto_increment</td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[zone_country_id](#countries)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[zone_id](#zones)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td>

[geo_zone_id](#geo_zones)</td>

<td class="db_td">int(11)</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td">MUL</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">last_modified</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">YES</td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

<tr class="db_tr">

<td class="db_td">date_added</td>

<td class="db_td">datetime</td>

<td class="db_td"></td>

<td class="db_td">NO</td>

<td class="db_td"></td>

<td class="db_td">0001-01-01 00:00:00</td>

<td class="db_td"></td>

<td class="db_td"></td>

</tr>

</tbody>

</table>

