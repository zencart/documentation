---
title: Shipping Modules
description: 
weight: 100 
layout: docs
---

{{% wip %}}

A shipping module class should use this basic skeleton.

e.g.

``` php
<?php
use Carbon\Carbon;
use Zencart\ModuleSupport\ShippingBase;
use Zencart\ModuleSupport\ShippingContract;
use Zencart\ModuleSupport\ShippingConcerns;

class flat extends ShippingBase implements ShippingContract
{
    use ShippingConcerns;

    public string $version = '1.0.0';
    public string $code = 'flat';
    public string $defineName = 'FLAT';

}

```

`$version` is not required, but if defined will be displayed with the title of the module in Admin.

`$code` should match the name of the module class.

`$defineName` is used to build setting defines. In the example of the flat shipping module and for a setting define with the prefix of `STATUS`

the define built would be `MODULE_SHIPPING_FLAT_STATUS`

As with other module types you can define a `addCustomConfigurationKeys` method along with `checkNonFatalConfigureStatus` and `checkFatalConfigureStatus`

methods where necessary.

