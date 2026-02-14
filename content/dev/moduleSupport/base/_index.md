---
title: Base Module Support
description: 
weight: 10
layout: docs
---

{{% wip %}}

# Introduction

The base module support classes contain common code that is used across all module types e.g Payments, Shipping and Order Total modules.

It also provides some common helper methods that you can use in your modules.

## Accessing Define Values

All module types store information about themselves in the database `configuration` table.

The `keys` for this table will look something like 

- MODULE_PAYMENT_COD_STATUS
- MODULE_SHIPPING_FLAT_COST
- MODULE_ORDERTOTAL_TOTAL_SORT_ORDER

The structure of these defines is  

MODULE_[module type]\_[module name]\_[define name]

where module type is one of `PAYMENT` or `SHIPPING` or `ORDERTOTAL`

The module name is taken from the $code class variable of the module, and the define name describes the purpose of the define. 

In previous versions of Zen Cart,these configuration values were accessed directly using the key that was stored in the database, however using 
the new module support classes we access them through a helper method.

e.g. In legacy code we might have done 

`$this->sort_order = defined('MODULE_PAYMENT_COD_SORT_ORDER') ? MODULE_PAYMENT_COD_SORT_ORDER : null;`

With the new infrastructure we can simply do 

`$this->sort_order = $this->getDefine('SORT_ORDER);`

The `getDefine` method is context aware, so knows which type of module you are using(PAYMENT/SHIPPING/ORDERTOTAL) and the current define name (e.g. COD) for 
the module you are using.

Furthermore, you can also set a value that will be returned from the method if the configuration value does not exist. 

In the example above, the method will return `null` if the `MODULE_PAYMENT_COD_SORT_ORDER` does not exist. 

However you could also do `$this->sort_order = $this->getDefine('SORT_ORDER, 0);`

and the method will return `0`, if the configuration value does not exist.

There are also a number of helper methods to get some of the most common module configuration keys. 

### getTitle

This gets the title for the Module. 

It looks for defines with suffixes in an array of ['TITLE', 'TEXT_TITLE', 'CATALOG_TITLE']

If your module uses a different define for the title then you should override the getTitle method.

### getAdminTitle

This returns a title to display on the Admin interface. In general this would be the same as the getTitle as above, but sometimes you may want it to be different.
It expects to be passed a default title, which would normally be what the getTitle function returns, and will use this if it does not find a define related to the admin title.

This function looks for defines with a suffix in an array ['TITLE_ADMIN', 'TEXT_TITLE_ADMIN', 'ADMIN_TITLE']

If your admin title is defined through other means, then you will need to override this method in your module.

### getDescription

returns a module define with the suffix `DESCRIPTION`  

### getSortOrder

returns a module define with the suffix `SORT_ORDER`  

### getZone

returns a module define with the suffix `ZONE`  

### getDebugMode

returns a module define with the suffix `DEBUG_MODE`  

### isEnabled

This function checks to see if the module is enabled.

it first checks to see if the module has any missing configurations and then check the module define suffix `STATUS`

### moduleAutoloadSupportClasses

This function is only called if it exists. 

It allows a module to add autoload classes using the psr4autoload Aura autoload.

e.g.

``` php
   protected function moduleAutoloadSupportClasses(Loader $psr4Autoloader): Loader
    {
        $psr4Autoloader->addPrefix('Stripe', DIR_FS_CATALOG . DIR_WS_MODULES . 'payment/stripe_pay/stripe-php-13.15.0/lib/');
        $psr4Autoloader->addPrefix('Monolog', DIR_FS_CATALOG . DIR_WS_MODULES . 'payment/stripe_pay/monolog/src/Monolog/');
        $psr4Autoloader->addPrefix('Zencart\Logger', DIR_FS_CATALOG . DIR_WS_MODULES . 'payment/stripe_pay/Logger/');
        return $psr4Autoloader;
    }
```
