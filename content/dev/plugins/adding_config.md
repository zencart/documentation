---
title: Adding a configuration setting 
description: How to add a new defined value to the database 
category: plugins
weight: 10
---

If you are creating a plugin or customizing some code, and you want to create a setting which can be changed in the admin without modifying code, you can put it in the database in an appropriate configuration group.  For example, a value relating to shipping should go in configuration group 7 (Shipping and Packaging).
 
```
INSERT INTO configuration (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, last_modified, date_added) VALUES ('Canada Shipping Surcharge', 'CANADA_SHIPPING_SURCHARGE', '12', 'Additional fee for shipping to Canada - added to quote from shipper', 7, 125, NULL, now());
```

Then, in your code, instead of hardcoding a number 

```
$shipping_cost += 12; 
```

refer to a configuration variable 

```
$shipping_cost += (float)CANADA_SHIPPING_SURCHARGE; 
```

Global settings should go in configuration group 1 (My Store).

```
INSERT INTO configuration (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, last_modified, date_added) VALUES ('Cut  Charge', 'PER_CUT_CHARGE', '1.25', 'Enter the cut charge', 1, 125, NULL, now());
```

## Distributing configuration changes 

If you are adding configuration data as part of a plugin for distribution, 
you can tell people to run a SQL file with your changes in the installation instructions, or you can do it automatically. 

To make configuration changes automatically, add a new function to `includes/functions/extra_functions` (or the same folder on the admin side), and do the operations there after verifying they haven't already been done. 

```

if (!defined('SPAM_TEST_TEXT')) {
    $db->Execute(
        "INSERT INTO " . TABLE_CONFIGURATION . " 
            (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, date_added, use_function, set_function) 
         VALUES 
            ( 'Hidden input field name.', 'SPAM_TEST_TEXT', 'should_be_273', 'You should change this field name like &quot;sams_cat&quot;.', '19', '501', now(), NULL, NULL)"
    );
... 
```
