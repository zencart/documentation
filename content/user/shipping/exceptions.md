---
title: Shipping Exceptions
description: How to disable shipping modules based on conditions
category: shipping 
weight: 10
---

Most shipping modules have a zone configuration setting, which allows you to 
disable the shipping module if the customer is not in the specified zone.

What if instead, you want to disable a shipping module based on the cart contents? 

Starting with Zen Cart 2.0.1, most shipping modules include a notifier in the `update_status` method (or a subordinate method) that allows you to set the `enabled` status. 

If you are running an earlier version of Zen Cart, this change is [easily backported](#backporting).


Here's an example observer that disables this module for product id 27.  (Obviously you will want to customize this for your specifications.)

Create the file `includes/classes/observers/auto.freeoptions.php` as follows: 
 

```

<?php
class zcObserverFreeoptions extends base
{
    public function __construct()
    {
        global $current_page_base;
        $this->attach(
            $this,
            [
                'NOTIFY_SHIPPING_FREEOPTIONS_UPDATE_STATUS',
            ]
        );
    }

    protected function update(&$class, $eventID, $not_used, &$enabled)
    {
        $products = $_SESSION['cart']->get_products();
        foreach($products as $product) {
            if ($product['id'] == 27) {

                $enabled = false; 
                return; 
            }
        }
    }
}
```

## Backporting

If you are running an earlier version of Zen Cart than 2.0.1, this change is easily backported.

For the built-in shipping modules, just download Zen Cart 2.0.1 or later, and copy the shipping module in question into your cart. 

Making the changes by hand is not difficult either; in the file you want to update, copy the notification from the version of that file in 2.0.1. (The notifiers are distinct for each shipping module, and contain the shipping module's name.)

For example, in the `flat` module, the notifier is `NOTIFY_SHIPPING_FLAT_UPDATE_STATUS`.  To backport, modify `includes/modules/shipping/freeoptions.php` and copy this call to the end of the `update_status` function.

The notifier looks like this: 

```
   if ($this->enabled) { 
       // -----
       // Give a watching observer the opportunity to disable the overall shipping module.
       //
       $this->notify('NOTIFY_SHIPPING_FLAT_UPDATE_STATUS', [], $this->enabled);
   }
```

And be sure the shipping module `extends base` - some earlier versions of some shipping modules do not:

```
  class flat extends base {
```
