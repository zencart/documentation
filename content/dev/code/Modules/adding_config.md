---
title: Adding New Configuration Values to a Module
description: Modifying module keys without requiring remove/reinstall
---

Over time, you may find that the initial set of configuration values for a module is not adequate.  For example, you want to add a new feature, which requires its own configuration, or a vendor (a shipper or a bank) may require additional data to authenticate the account. 

## Warning on Missing Configuration Values 

The old way of handling this situation was to ask the user to REMOVE the module, and then run the INSTALL again.  

In the USPS plugin, for example, 

```
            if (MODULE_SHIPPING_USPS_VERSION != self::USPS_CURRENT_VERSION || count($this->keys()) != $chk_sql->RecordCount()) {
                $this->title .= '<span class="alert">' . ' - Missing Keys or Out of date you should reinstall!' . '</span>';
                $this->enabled = false;
            }
```

Remove and re-install was annoying for users, and error prone in cases where modules had large and complicated configuration. 

## Dynamically Handling Missing Configuration Values 

To detect and recover from this condition, the newer way is to simply add the configuration settings in the `check()` method.   (Note that some older modules use the `keys()` method for this purpose; either method is acceptable.)

Care must be taken to ensure that the module is already installed (check the `_STATUS` setting) so that the config won't be added twice when an the `install` method is run. 

From paypalwpp.php line 704 in Zen Cart 1.5.7d, 


```
    if (defined('MODULE_PAYMENT_PAYPALWPP_STATUS')) {
      global $db;
      if (!defined('MODULE_PAYMENT_PAYPALWPP_ECS_BUTTON')) {
        $db->Execute("INSERT INTO " . TABLE_CONFIGURATION . " (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, set_function, date_added) VALUES ('Express Checkout Shortcut Button', 'MODULE_PAYMENT_PAYPALWPP_ECS_BUTTON', 'On', 'The Express Checkout Shortcut button shows up on your shopping cart page to invite your customers to pay using PayPal without having to give all their address details on your site first before selecting shipping options.<br />It has been shown to increase sales and conversions when enabled.<br />Default: On ', '6', '25', 'zen_cfg_select_option(array(\'On\', \'Off\'), ', now())");
      }
...
```
