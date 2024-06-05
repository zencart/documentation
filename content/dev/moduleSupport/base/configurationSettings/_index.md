---
title: Configuration Settings
description: 
weight: 80
layout: docs
---

{{% alert title="Warning" color="warning" %}}
The documentation in this section is Work in progress and relates to features that might not be available yet.
{{% /alert %}}

# Introduction

In Zen Cart modules written before this module infrastructure code, configuration settings used SQL statements for those settings.

This was usually done in a module method called `install` and would look something like. 

``` php 
    function install() {
      global $db, $messageStack;
      if (defined('MODULE_PAYMENT_FREECHARGER_STATUS')) {
        $messageStack->add_session('FreeCharger module already installed.', 'error');
        zen_redirect(zen_href_link(FILENAME_MODULES, 'set=payment&module=freecharger', 'SSL'));
        return 'failed';
      }
      $db->Execute("insert into " . TABLE_CONFIGURATION . " (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, set_function, date_added) values ('Enable Free Charge Module', 'MODULE_PAYMENT_FREECHARGER_STATUS', 'True', 'Do you want to accept Free Charge payments?', '6', '1', 'zen_cfg_select_option(array(\'True\', \'False\'), ', now());");
      $db->Execute("insert into " . TABLE_CONFIGURATION . " (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, date_added) values ('Sort order of display.', 'MODULE_PAYMENT_FREECHARGER_SORT_ORDER', '0', 'Sort order of display. Lowest is displayed first.', '6', '0', now())");
      $db->Execute("insert into " . TABLE_CONFIGURATION . " (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, use_function, set_function, date_added) values ('Payment Zone', 'MODULE_PAYMENT_FREECHARGER_ZONE', '0', 'If a zone is selected, only enable this payment method for that zone.', '6', '2', 'zen_get_zone_class_title', 'zen_cfg_pull_down_zone_classes(', now())");
      $db->Execute("insert into " . TABLE_CONFIGURATION . " (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, set_function, use_function, date_added) values ('Set Order Status', 'MODULE_PAYMENT_FREECHARGER_ORDER_STATUS_ID', '0', 'Set the status of orders made with this payment module to this value', '6', '0', 'zen_cfg_pull_down_order_statuses(', 'zen_get_order_status_name', now())");
    }

```

With the new module infrastructure code this is simplified. 

The base module classes define a default set of configurations settings for payment/shipping/order total classes, and 3rd party modules can add to those settings. 

Rather than use SQL statements, we now use an array based method of defining the settings. 

If a module needs to add extra settings, it should define a method called `addCustomConfigurationKeys`

An example, taken from a rewritten moneyorder payment module.

```php
    protected function addCustomConfigurationKeys(): array
    {
        $configKeys = [];
        $key = $this->buildDefine('PAYTO');
        $configKeys[$key] = [
            'configuration_value' => 'the Store Owner/Website Name',
            'configuration_title' => 'Make Payable to:',
            'configuration_description' => 'Who should payments be made payable to?',
            'configuration_group_id' => 6,
            'sort_order' => 1,
        ];
        return $configKeys;
    }
```

## Module Settings Keys

The following is a list of module settings keys and their usage as per the `configuration` database table.

### configuration_title

### configuration_key

### configuration_value

### configuration_description

### sort_order

### last_modified

### date_added

### use_function

### set_function

### val_function


