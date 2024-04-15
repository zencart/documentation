---
title: Writing Payment Modules
description: 
weight: 5
---

## Introduction

{{% alert title="Warning" color="warning" %}}
This documentation refers to upcoming changes that may not have been implemented yet
{{% /alert %}}

Zen Cart V2+ introduces a new way to write payment modules. The structure has been simplified, with base classes 
carrying out default code. This should make writing new payment modules much easier, with less copy/pasting.

To create a basic payment module skeleton, you need to create a class inside the `includes/modules/payment/` directory. The 
payment class should have a unique name. In examples here we are going to use 'moneyorder' as the class name. 

```
<?php

use Carbon\Carbon;
use Zencart\ModuleSupport\PaymentModuleAbstract;
use Zencart\ModuleSupport\PaymentModuleContract;
use Zencart\ModuleSupport\PaymentModuleConcerns;

class moneyorder extends PaymentModuleAbstract implements PaymentModuleContract
{
    use PaymentModuleConcerns;

    public string $email_footer = "";

    protected const CURRENT_VERSION = '1.0.0-alpha';
    public string $MODULE_ID = 'MONEYORDER';
    public string $code = 'moneyorder';
}
```

There are a couple of things you need to customize here. 

`protected const CURRENT_VERSION = '1.0.0-alpha';`

This is not required but setting this can help users of your module know which version they are using.

`public string $MODULE_ID = 'MONEYORDER';`

This is required, and is a unique key for your payment module. It should always be upper case.

`public string $code = 'moneyorder';`   

This is required and should generally be the same as the class name for your payment module.

The interface for the payment module also requires you to create a method in your class called 

`addCustomConfigurationKeys`

This method creates custom configuration keys for your payment module on top of the default configureation keys that are needed.

See [Payment Module Configuration Keys]()

Payment modules will also need to create their own language file. 
e.g. `includes/languages/english/modules/payment/lang.moneyrder.php`

See [Payment Module Language Files]()
