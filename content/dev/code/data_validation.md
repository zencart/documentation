---
title: Configuration Data Validation - About
description: How is data validation done for configuration values? 
category: code
type: codepage
weight: 10
---

Fields in the configuration table have self-contained validation instructions in the `val_function` field.

The `val_function` field is described in JSON format, with an error message in case validation fails, the id of the validation to be performed, and a set of options for validation.  This syntax is based on the calling conventions for [filter_var](https://www.php.net/manual/en/function.filter-var.php). 

```
{
  "error":"TEXT_MAX_PREVIEW",
  "id":"FILTER_VALIDATE_INT",
  "options":{"options":{"min_range":0}}
}
```

The list of `id` values and possible options for each are shown in the PHP documentation on [filters](https://www.php.net/manual/en/filter.filters.validate.php). 

### Adding validation to a custom config

Suppose you want to do a check in your cart of an order's value, and only offer PayPal as an option for orders under a certain value.  If you hardcode this threshold, you'll have to change and re-deploy code any time you want to change it.  Storing it in the configuration table is a better idea.  So you add it: 

```
INSERT INTO configuration (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, last_modified, date_added, use_function, set_function) VALUES ('Max PayPal','MAX_PAYPAL','4000','Enter max total which can use PayPal.  Must be &lt; $10K, per PayPal rules.',1,100,NULL,now(),NULL,NULL)
```
But then you decide you want to add validation, so that this value is ranged between 4000 and 9999. 

To do this, you'd use the SQL statement 

```
UPDATE configuration SET val_function = 
'{"error":"TEXT_MAX_PAYPAL","id":"FILTER_VALIDATE_INT","options":{"options":{"min_range":4000, "max_range":9999}}}'
WHERE configuration_key = 'MAX_PAYPAL'; 
```

Where `TEXT_MAX_PAYPAL` is defined in a globally accessible admin language file like `admin/includes/languages/english/extra_definitions/my_errors.php` 

```
<?php
define('TEXT_MAX_PAYPAL','Max PayPal must be in the range 4000-9999'); 
```

Now when an administrator attempts to set it outside this range, an error will be shown at the top of the admin screen like this: 

<img src="/images/validation_error.png" alt="Zen Cart admin data validation error" width="50%" />
<br><br>

### Validating Module Data
As of Zen Cart 1.5.7, you can also perform validation on fields in your shipping, payment and order total modules.  

Use the same `val_function` format.  The error defines need to be global (not just local to your module).  For convenience, the following strings are provided for common validations (integer >= 0 and floating point value >= 0): 

```
define('TEXT_POSITIVE_INT','%s must be an integer greater than or equal to 0');
define('TEXT_POSITIVE_FLOAT','%s must be a decimal greater than or equal to 0'); 
```

Note that they take a parameter, which is passed in by the core; it's the name of the setting being validated.  This is important for modules because unlike configuration values, multiple settings are done at once. 

If you prefer, define an error string of your own and place it in a file in `admin/includes/languages/english/extra_definitions`.

See the `flat` shipping module for an example. 

<br><br>

The `val_function` field was added in Zen Cart 1.5.6, but not widely used until Zen Cart 1.5.7. 
