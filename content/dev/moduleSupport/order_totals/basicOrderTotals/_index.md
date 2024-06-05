---
title: Basic Order Total Modules
description: 
weight: 100
layout: docs
---

These modules are fairly simple and provide minimal interaction in the checkout, and are usually used to aggregate values.

examples would be

- calculate/display the order sub total (e.g. the total of all product costs)
- calculate/display the total tax for the order 
- calculate/display the total shipping cost for the order
- calculate/display a simple low order fee

A basic order total module should use this basic skeleton, adjusting the class name and class variables where appropriate.

``` php 
<?php

use Zencart\ModuleSupport\OrderTotalBase;
use Zencart\ModuleSupport\OrderTotalConcerns;
use Zencart\ModuleSupport\OrderTotalContract;

class ot_total extends OrderTotalBase implements OrderTotalContract
  {
    use OrderTotalConcerns;

    public string $version = '1.0.0'
    public string $code = 'ot_total';
    public string $defineName = 'TOTAL';

  }
```

`$version` is not required, but if defined will be displayed with the title of the module in Admin.

`$code` should match the name of the module class.

`$defineName` is used to build setting defines. In the example of the ot_total module and for a setting define with the prefix of `STATUS`

the define built would be `MODULE_ORDERT_TOTAL_TOTAL_STATUS`

As with other module types you can define a `addCustomConfigurationKeys` along with `checkNonFatalConfigureStatus` and `checkFatalConfigureStatus`

where necessary.
