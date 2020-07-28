---
title: Tracking Inventory 
description: Stock Management in Zen Cart 
category: Running
weight: 10
---

Several options exist for inventory tracking.  See 
[Admin > Configuration > Stock](/user/admin_pages/configuration/configuration_stock/) for details.

Common configurations are: 

### Don't track stock

```
Check stock level = false 
Subtract stock = false 
Allow Checkout  = true 
```

### Track stock, but permit backorders 
```
Check stock level = true 
Subtract stock = true 
Allow Checkout  = true 
```

### Track stock, do not permit backorders 
```
Check stock level = true 
Subtract stock = true 
Allow Checkout  = false
```

