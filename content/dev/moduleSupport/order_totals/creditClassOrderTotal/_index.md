---
title: Credit Class Modules
description: 
weight: 120
layout: docs
---

These modules usually involve some interaction during checkout and also add options to allow for more complex tax calculations.

examples would be 

- Group Pricing
- Discount Coupons
- Gift Vouchers
- Reward points modules

The skeleton for these credit class order total modules would be

``` php
<?php
 use Zencart\ModuleSupport\OrderTotalCCBase;
 use Zencart\ModuleSupport\OrderTotalCCConcerns;
 use Zencart\ModuleSupport\OrderTotalCCContract;

class ot_group_pricing extends OrderTotalCCBase implements OrderTotalCCContract
{

  use OrderTotalCCConcerns;

  public string $version = '1.0.0';

  public string $code = 'ot_group_pricing';

  public string $defineName = 'GROUP_PRICING';

 }
 ```

`$version` is not required, but if defined will be displayed with the title of the module in Admin.

`$code` should match the name of the module class.

`$defineName` is used to build setting defines. In the example of the ot_group_pricing module and for a setting define with the prefix of `STATUS`

the define built would be `MODULE_ORDER_TOTAL_GROUP_PRICING_STATUS`

As with other module types you can define a `addCustomConfigurationKeys` along with `checkNonFatalConfigureStatus` and `checkFatalConfigureStatus`

where necessary.
