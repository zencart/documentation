---
title: Language defines
description: 
weight: 120
layout: docs
---

{{% wip %}}

Language define files for modules follow the same format as normal array based language defines.

They are stored in `includes/languages/{language}/modules/` and at the very least should have an english translation. 

e.g. 

`includes/languages/english/modules/payment/lang.cod.php`

`includes/languages/english/modules/shipping/lang.flat.php`

`includes/languages/english/modules/order_total/lang.ot_subtotal.php`


Like module configuration keys, naming of module language defines are the same 
e.g. 

`MODULE_[module type]\_[module name]\_[define name]`

There are some other rules.

language define names should be unique and not match any other module configuration defines. 

At a minimum you should provide the following 

`'TEXT_TITLE' => 'Stripe Checkout',`
 
`'TEXT_DESCRIPTION' => '<strong>Stripe Pay</strong>',`


e.g 

``` php
$define = [
    'MODULE_PAYMENT_STRIPE_PAY_TEXT_TITLE' => 'Stripe Checkout',
    'MODULE_PAYMENT_STRIPE_PAY_TEXT_DESCRIPTION' => '<strong>Stripe Pay</strong>',
];
return $define;
```

Note: also if you want to provide a different tiile in the admin interface you can add something like 

`MODULE_PAYMENT_STRIPE_PAY_TEXT_TITLE_ADMIN' => 'Stripe Checkout(ADMIN)`

