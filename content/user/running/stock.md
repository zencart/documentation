---
title: Tracking Inventory 
description: Stock Management in Zen Cart 
category: Running
weight: 10
---

Many options exist for inventory tracking.  See 
[Admin > Configuration > Stock](/user/admin_pages/configuration/configuration_stock/) for details.

Common configurations are: 

### 1. Don't track stock

```
Check stock level = false 
Subtract stock = false 
Allow Checkout  = true 
```

This configuration is well suited for stores that sell virtual products, which can't be depleted. 

### 2. Track stock, but permit backorders 
```
Check stock level = true 
Subtract stock = true 
Allow Checkout  = true 
```

This configuration is ideal for stores that sell products where manufacturers can fill re-orders easily and out-of-stock or discontinuation situations are unlikely. 

### 3. Track stock, do not permit backorders 
```
Check stock level = true 
Subtract stock = true 
Allow Checkout  = false
```

This configuration would be a good match for stores that sell unique or limited quantity products, such as artisan produced goods. 

### Status handling for Subtract stock = true

Stores that track stock (i.e. have Subtract stock = true) also need to decide on whether changes are required to the [status of a product](/user/products/products_status/) when the quantity in stock goes to zero. 

The configuration setting `Products status in Catalog when out of stock should be set to` controls this.  When set to 0, a product will change status to Disabled when the last one is sold.  When set to 1, no status change will occur. 

## What about Variant Stock? 

At the current time, Zen Cart does not track the stock of individual product variants (a t-shirt's stock of large versus medium, for example).  There are commercial modifications that address this requirement however, such as 
the [Products' Options' Stock Manager (POSM)](https://vinosdefrutastropicales.com/product_extra_files/options_stock/readme.html). 

