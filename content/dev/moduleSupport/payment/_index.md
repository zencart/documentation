---
title: Payment Modules
description: 
weight: 100 
layout: docs
---

{{% alert title="Warning" color="warning" %}}
The documentation in this section is Work in progress and relates to features that might not be available yet.
{{% /alert %}}

A payment module class should use this basic skeleton.

e.g.

``` php
<?php

use Zencart\ModuleSupport\PaymentBase;
use Zencart\ModuleSupport\PaymentContract;
use Zencart\ModuleSupport\PaymentConcerns;

class moneyorder extends PaymentBase implements PaymentContract
{
    use PaymentConcerns;

    public string $version = '1.0.0';
    public string $code = 'moneyorder';
    public string $defineName = 'MONEYORDER';
}

```

`$version` is not required, but if defined will be displayed with the title of the module in Admin.

`$code` should match the name of the module class.

`$defineName` is used to build setting defines. In the example of the moneyorder payment module and for a setting define with the prefix of `STATUS`

the define built would be `MODULE_PAYMENT_MONEYORDER_STATUS`

As with other module types you can define a `addCustomConfigurationKeys` along with `checkNonFatalConfigureStatus` and `checkFatalConfigureStatus`

where necessary.
