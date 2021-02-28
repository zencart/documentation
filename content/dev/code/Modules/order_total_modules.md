---
title: Order Total Modules
description: Adding fees and discounts to an order 
---
<style>
pre > code {
white-space: pre-wrap !important;
}
</style>
# Introduction
Zen Cart *order-total* modules are used to calculate (and display) sub-totals, taxes, totals and other intermediary values for an order. *Order-total* modules can also calculate discounts or other subtractions from the amount a customer owes for an order. Each module includes, at a minimum, two files:

1. A `class` file: /includes/modules/order_total/`my_order_total`.php
1. A `language` file: /includes/languages/`current_language`/modules/order_total/`my_order_total`.php

The `language` file contains all the translatable language text for the module while the `class` file contains the module's processing portion.

## Order Total Class
The class defined in `/includes/classes/order_total.php` handles the loading of the *order-total* modules during Zen Cart storefront order-processing.

## Anatomy of an Order-Total Module
Each module can provide either *basic* or *credit-class* computations.  *Credit-class* modules, like the Coupon (`ot_coupon`) or Gift Certificate (`ot_gv`) built into the Zen Cart base, can also operate on customer input during the checkout process.

### Class Names
An *order-total* module's filename (e.g. `my_order_total`.php) is also used as its class name:
```php
class my_order_total extends base
{
  ...
}
```
**Note:** Unlike *shipping* modules, underscore characters `(_)` **are** allowed in *order-total* module names!


### Class Variables
An *order-total* module's class definition includes the following publicly-available variables, depending on the "mode" in which the order-total processes:

Variable Name | Variable Type | Basic | Credit Class | Description
------------- | -------------- | :----: | :------------: | -------------
code | string | &check; | &check; | Contains the unique "code" identifying this order-total; normally set to the module's class name.
title | string | &check; | &check; |Identifies the title displayed for the module during the admin's *Modules > Order Total* processing.  This variable is normally initialized during class construction to a language-file definition.
description | string | &check; | &check; | Identifies the description displayed for the module during the admin's *Modules > Order Total* processing.  This variable is normally initialized during class construction to a language-file definition.
sort_order | integer | &check; | &check; | Identifies the *relative* order in which this module is processed; the value configured must be unique within a store's *Modules > Order Total* settings.  This value is used by the main `order_total` class (`/includes/classes/order_total.php`), which loads all active modules in  ascending `sort_order` sequence.
output | array | &check; | &check; | Contains the order-total's "output", a PHP associative array containing the information to be displayed in an "orders-totals" section, e.g. on the `checkout_confirmation page`.  See below for details. 
credit_class | boolean | &mdash; | &check; | Identifies, if present and set to boolean *true*, that the module **is** a credit-class object.  When a module indicates that it performs `credit_class` processing, that *order-total* module provides additional class methods.

The order-total's `output` array contains the following fields:

Array "Key" | Type | Array "Value"
----------- | ----- | --------
title | string | The descriptive text to accompany the module's addition to (or subtraction from) the order.
value | float | The numeric value that the module applies to the order.  Positive values add; negative values subtract.
text | string | The character-display value associated with the module's numeric `value`.  This value is normally created via call to the Zen Cart `$currencies` class and represents the currency-formatted `value`.


### Class Methods
The methods provided by an *order-total* module depend on whether the module provides credit-class processing.

#### Basic Order-Total Class Methods
These methods are provided by all *order_total* modules.

-------
##### __construct
A module's class-constructor method performs initialization of its class variables and determines whether the module is enabled for the current order.  Upon completion, the class variable `enabled` identifies whether (*true*) or not (*false*) the module is to be enabled for storefront processing.
```php
class my_order_total extends base
{
    public function __construct ()
    {
    }

    ...
}
```

-------
##### process
This method, normally called during the *confirmation* and *processing* phases of the checkout process, performs the module's special calculations.  If the module's conditions are satisfied, the module adds (or subtracts) its cost from the order's current total and, optionally, makes any tax-related adjustments to the order's tax.

Basic `process` function processing is illustrated below.

```php
class my_order_total extends base
{
    ...
    public function process ()
    {
        global $order, $currencies;

        ...

        if ($this_totals_conditions_are_satisified) {
            $order->info['total'] += $my_cost;
            $this->output[] = array (
                'title' => $this->title,
                'value' => $my_cost,
                'text' => $currencies->format ($my_cost, true,  $order->info['currency'], $order->info['currency_value']),
            );
        }
    }

    ...
}
```
-------
##### check
This method, called from admin-level *Modules > Order Total* processing, returns a boolean value indicating whether (true) or not (false) the module is currently installed.
```php
class my_order_total extends base
{
    ...

    public function check ()
    {
        global $db;
        if (!isset ($this->_check)) {
            $check_query = $db->Execute ("SELECT configuration_value FROM " . TABLE_CONFIGURATION . " WHERE configuration_key = 'MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_STATUS' LIMIT 1");
            $this->_check = !$check_query->EOF;
        }
        return $this->_check;
    }

    ...
}
```
-------
##### install
This method, called from admin-level *Modules > Order Total* processing when the module is initially installed, sets the module's configuration into the Zen Cart database.  The example shows how to insert the common, required, configuration elements into the database for the `my_order_total` order-total module.  If your *order-total* module requires additional settings, add them here.
```php
class my_order_total extends base
{
    ...

    public function install () 
    {
        global $db;

        $db->Execute ("INSERT INTO " . TABLE_CONFIGURATION . " (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, set_function, date_added) VALUES ('Enable My Order Total', 'MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_STATUS', 'True', 'Do you want to enable "my order total" processing?', '6', '0', 'zen_cfg_select_option(array(\'True\', \'False\'), ', now())");
        $db->Execute ("INSERT INTO " . TABLE_CONFIGURATION . " (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, date_added) VALUES ('Sort Order', 'MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_SORT_ORDER', '400', 'Sort order of display.', '6', '0', now())");

        ...

    }

    ...

}
```
-------
##### keys
This method, called during admin-level *Modules > Order Total* processing, returns the database configuration "keys" associated with this *order-total* module.  The configuration values are displayed for the module *in the order specified by the returned array*.
```php
class my_order_total extends base
{
    ...

    public function keys () 
    {
        return array (
            'MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_STATUS', 
            'MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_SORT_ORDER'
        );
    }

    ...

}
```
-------
##### remove
This method, called during admin-level *Modules > Order Total* processing to remove this module, removes all database changes (*normally* just configuration keys) associated with the *order-total* module.
```php
class my_order_total extends base
{
    ...

    public function remove () 
    {
        global $db;
      	$db->Execute ("DELETE FROM " . TABLE_CONFIGURATION . " WHERE configuration_key LIKE 'MODULE\_ORDER_TOTAL\_MY_ORDER_TOTAL\_%'");
    }

    ...

}
```

#### *Credit-Class* Order-Total Methods
These methods are provided by an *order-total* module that identifies itself as a *Credit Class* module by setting its `$this->credit_class` variable to *true*.  The *Coupon* (ot_coupon) and *Gift Voucher* (ot_gv) modules that are built into Zen Cart are examples of this type of *order-total* module.

**Note:** While many of the *credit-class* order-total modules include a method named `pre_confirmation_check`, that method is never called during the checkout process and can be safely removed (if not used internally).

-------
##### credit_selection
This method, normally called during the *payment* stage of the checkout process, returns an associative array containing information describing any form-related elements associated with the module's processing.  If the module has no value to return for the current order, an empty array *should be* returned.

The module is given the opportunity to process these fields via future call to its `collect_posts` method.

The `selection` array returned uses the following structure:

Field Name | Type | Description
---------- | ---- | -----
id | string | Normally set to the current module's "code", e.g. `ot_my_order_total`.
module | string | Normally set to the current order-total's descriptive name.  This value is displayed to the customer.
redeem_instructions | string | Normally set to a language-constant, describes to the customer what the module does and how its processed.
checkbox | string | Normally set to a text string containing HTML tags required for some special processing by the module.
fields | array | A basic array containing one array-element for each customer-configurable input field used in this module's processing.

Each `fields` array element is also an associative array, using the following structure:

Field Name | Type | Description
---------- | ---- | ---
title | string | The text to display for any HTML `label` associated with the current field.
field | string | The HTML input tag used to gather this field's input.
tag | string | Identifies, if non-blank, the value to be used for the `for` attribute of the generated `label` tag.

```php
class my_order_total extends base
{
    ...

    public function credit_selection () 
    {
        $input_field_id = 'disc-' . $this->code;
        $selection = array (
            'id' => $this->code,
            'module' => $this->title,
            'redeem_instructions' => MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_REDEEM_INSTRUCTIONS,
            'fields' => array (
                'title' => MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_ENTER_CODE,
                'field' => zen_draw_input_field ('my_redeem_code', '', 'id="' . $input_field_id . '"'),
                'tag' => $input_field_id
            ),
        );
        return $selection;
    }

    ...

}
```

-------
##### collect_posts
This method is called during the *payment* and *confirmation* stages of the checkout process, allowing a module to gather, inspect and process the `$_POST` variables that it identified by its `credit_selection` method's return.  The method returns no value.

If the *order-total* module's processing discovers an issue with the posted information, it is the module's responsibility to display a message to the customer to describe the problem and redirect back to the `checkout_payment` page to allow the form-input to be re-displayed and updated by the customer.

```php
class my_order_total extends base
{
    ...

    public function collect_posts () 
    {
       ...
    }

    ...

}
```

-------
##### update_credit_account
This method is called during the *processing* stage of the checkout process by the `order` class' `create_add_products` function *for each product iteration*, enabling an *order-total* module to have "visibility" into the specific products that are in the order.

The method's purpose is to allow a module to decide whether the current product in the order should add something to a credit account.  For example, for the *Gift Voucher* processing, a check is made to see if the product is a *Gift Voucher* and then adds the GV amount to the customer's GV account.  Another use would be to check to see if the product would give reward-points and add those points to the customer's points/reward account


The method's input is the integer index into the current order's `products` array and the method returns no direct output.

```php
class my_order_total extends base
{
    ...

    public function update_credit_account ($i) 
    {
        global $order;
        if ($order->products[$i]['name'] == 'Some Special Text') {
           ...
        }
    }

    ...

}
```

-------
##### apply_credit
This method is called during the *processing* stage of the checkout process by the `order` class' `create_add_products` method just prior to that method's completion.  The method takes no direct input and returns no direct value.

The method's purpose is to enable a module to test whether the customer has chosen to apply a credit amount to their order, reducing the order's final total.  If so, the *order-total* module's processing performs some action, e.g. for a *Gift Voucher*, the customer's GV account is reduced by the amount applied to the order.

```php
class my_order_total extends base
{
    ...

    public function apply_credit () 
    {
       ...
    }

    ...

}
```

-------
##### clear_posts
This method is called during the *processing* stage of the checkout process and gives a module the opportunity to remove any session-related information for the just-completed order.  The method neither takes nor returns any direct values.

```php
class my_order_total extends base
{
    ...

    public function clear_posts () 
    {
       unset ($_SESSION['my_redeem_code']);
    }

    ...

}
```

### *Standard* Configuration Settings
These common settings *should be* provided by all *order-total* modules:

Configuration Name | Configuration Value
------------------ | ------------------------------------------------
`MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_STATUS` | Set to either 'true' or 'false', identifies whether or not the module is currently enabled.
`MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_SORT_ORDER` | Identifies the sort-order to be used when displaying this module.

### Tips & Tricks
Procedurally, all configuration options for an *order-total* module named `my_order_total` should be named `MODULE_ORDER_TOTAL_MY_ORDER_TOTAL_*`, as should all language constants for the module, to ensure uniqueness of those constants.

### Troubleshooting
Since the admin-level processing by *Modules > Order Total* loads all `.php` modules present in the `/includes/modules/order_total` folder, make sure that any backup files in that directory have the `.php` extension are renamed (use `.php.bak` or `.php~`), or errors will result during the admin loading.
