---
title: Tracking Inventory 
description: Stock Management in Zen Cart 
category: Running
weight: 10
---

Several options exist for inventory tracking.  See 
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

