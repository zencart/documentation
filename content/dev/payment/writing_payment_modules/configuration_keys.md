---
title: Configuration keys
description: 
weight: 5
---

Payment modules use configuration keys to store the settings for that payment module.

The payment module classes set up some default configuration keys, but it is expected that a module writer will need 
to set up some of their own keys/settings.

## Default  Keys

The default keys that the system sets up are :-

 - MODULE_PAYMENT_%%_STATUS

   Whether that module is enabled or not

 - MODULE_PAYMENT_%%_SORT_ORDER

   The order that the module appears in both the admin and the catalog
 - 
 - MODULE_PAYMENT_%%_ZONE

   Payment modules can be rerstricted to a certain geographic zone

 - MODULE_PAYMENT_%%_DEBUG_MODE

   If debug mode is enabled then log files will be created.

## Custom keys

Most payment modules will need to create their own custom keys/settings. 

to do this the module must add a protected method to its class. 

e.g. 

```angular2html
    protected function addCustomConfigurationKeys(): array
    {
        $configKeys = [];
        $key = $this->buildDefine('MODULE_PAYMENT_%%_PAYTO');
        $configKeys[$key] = [
            'configuration_value' => 'the Store Owner/Website Name',
            'configuration_title' => 'Make Payable to:',
            'configuration_description' => 'Who should payments be made payable to?',
            'configuration_group_id' => 6,
            'sort_order' => 1,
            'last_modified' => null,
            'date_added' => Carbon::now(),
            'use_function' => null,
            'set_function' => null,
            'val_function' => null,
        ];
        return $configKeys;
    }
```

Note: 

Even if you don't need any custom settings, you must still add this method. 

e.g. 

```
    protected function addCustomConfigurationKeys(): array
    {
        return [];
    }
```
