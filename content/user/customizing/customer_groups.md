---
title: Using Customer Groups
description: Customizing your site using Customer Groups 
category: customizing 
weight: 10
---

Note: These ideas take advange of the 1.5.8 feature [Customer Groups](/user/admin_pages/customers/customer_groups/), so they will only be applicable to Zen Cart 1.5.8 and above.

## Restricting page to a Customer Group 

See [Protecting Pages](/user/customizing/protecting_pages/#restricting-page-to-a-customer-group). 

## Restricting a Shipping Method to a Customer Group 

In the `__construct` method of the shipping module, below the other checks for enabled, add 

```
     if (IS_ADMIN_FLAG !== true) { 
       $allowed_group = 1; 
       if (!(zen_is_logged_in() && zen_customer_belongs_to_group((int)$_SESSION['customer_id'],$allowed_group, true))) {
          $this->enabled = false;
       } 
     } 
```

## Restricting a Payment Method to a Customer Group 

In the `__construct` method of the payment module, below the check which ensures `sort_order` is set, add 

```
     if (IS_ADMIN_FLAG !== true) { 
       $allowed_group = 1; 
       if (!(zen_is_logged_in() && zen_customer_belongs_to_group((int)$_SESSION['customer_id'],$allowed_group, true))) {
          return false; 
       } 
     } 
```

