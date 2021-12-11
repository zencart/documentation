---
title: Start and End Dates
description: Automatically starting and stopping Sales or Specials 
category: categories
weight: 10
---

## Sales and Specials 
Both [Specials](/user/products/special_products/) and [Sales](/user/products/sale_products/) have configurable start and end dates, which means you don't have to turn them off or on by hand if you don't want to.  

Here's how they work: 
- On every page load (admin or storefront), the current date is determined using the [cart's timezone](/user/new_user_topics/timezone/). 
- Any *currently disabled* Sales or Specials are **enabled** if they have: 
  - they have a start date which is less than or equal to the current date (or start date not set), 
  - they have an end date which is greater than the current date (or end date not set) 
- Any *currently enabled* Sales or Specials are **disabled** if: 
  - the current date is less than the start date (if start date set)  
- Any *currently enabled* Sales or Specials are **disabled** if: 
  - the current date is greater than or equal to the end date (if the end date is set). 
  - the current date is less than the start date (if the end date is set). 

So a sale with a start date of 01/27/2021 and an end date of 01/28/2021 would run from only on 01/27/2021.  As soon as the date changed, the sale would end.  (The actual database update ending the sale would occur on the first page load after 01/28/2021 began.)

## Featured Products 

[Featured Products](/user/admin_pages/catalog/featured/) also have a start and end date, and work the same way Sales and Specials do, as described above.

## Upcoming Products 

Since Zen Cart 1.5.7, it has been possible to automatically enable any disabled [Upcoming Product](/user/products/upcoming_products/) on its available date, 
using the [enable disabled product by available date](/user/admin_pages/configuration/configuration_stock/#enable_disabled_product_by_available_date) feature. 
