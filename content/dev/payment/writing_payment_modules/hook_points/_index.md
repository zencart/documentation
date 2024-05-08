---
title: Hook Methods
description: 
weight: 10
---

The payment module system has various methods that can be overriden to allow your payment module to 
hook into the checkout lifecycle.

This allows you to leverage the API's that payment providers provide to give your customers a ....

## __construct method

When a payment module class is initially created, it runs the __construct method. This method is provided in the underlying 
payment infrastructure and does a number of actions to initiate a class.  

In general you may not need to override this method but the inbuilt `moneyorder` module provides an example of adding a warning if the 
`MODULE_PAYMENT_MONEYORDER_PAYTO` setting has not been set, and also adds a setting for an email footer. 

e.g. 

```
    public function __construct()
    {
        parent::__construct();
        if (IS_ADMIN_FLAG !== true) {
            return;
        }
        if ($this->enabled === false) {
            return;
        }

        if ($this->getDefine('MODULE_PAYMENT_%%_PAYTO') == 'the Store Owner/Website Name' || $this->getDefine('MODULE_PAYMENT_%%_PAYTO') == '') {
            $this->title .= '<span class="alert"> (not configured - needs pay-to)</span>';
        }
        $this->email_footer = MODULE_PAYMENT_MONEYORDER_TEXT_EMAIL_FOOTER;
    }

```

In the above we first call the parent __construct method to ensure inital setup happens, then adjust the `title` setting if the `PAY_TO` setting has not been customised
