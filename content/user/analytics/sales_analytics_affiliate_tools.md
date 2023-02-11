---
title: Integrating Sales Analytics/Affiliate Tools
description: JROX JAM, SNAP, iDevAffiliate and other sales tracking systems 
category: analytics
weight: 10
type: codepage
aliases:
    - /user/orders/sales_analytics_affiliate_tools/
---

On the "checkout_success" page, there are several pieces of data available:  

*   **$order_summary['order_number']** = The current order number
*   **$order_summary['order_subtotal']** = The subtotal of the price of all products in the cart, before shipping etc
*   **$order_summary['credits_applied']** = A sum of all discounts/credits applied to the order (ie: handled by "credit" order total modules such as coupons, gift certificates and customer-group-discounts)
*   **$order_summary['commissionable_order']** = The amount of the purchase that is commissionable, ie: subtotal minus discounts
*   **$order_summary['commissionable_order_formatted']** = Formatted according to the current currency
*   **$order_summary['coupon_code']** = The coupon code used in this order, if any
*   **$order_summary['currency_code']** = The currency used when making this sale
*   **$order_summary['currency_value']** = The exchange rate applied while using this currency
*   **$order_summary['payment_module_code']** = The payment module used to facilitate payment
*   **$order_summary['shipping_method']** = The shipping method selected by the customer
*   **$order_summary['orders_status']** = The status number denoting the order's status in the system
*   **$order_summary['tax']** = The amount of tax on the order
*   **$order_summary['shipping']** = The shipping cost
*   **$order_summary['order_total']** = The final/net total of the order, the amount for payment  
    Also available starting with ZC v1.5.5 are the following (or add them to older versions using the extra PHP code shown below the following examples)
*   **$order_summary['products_ordered_models']** = a list of product model numbers, delimited by '|'
*   **$order_summary['products_ordered_ids']** = a list of product ID numbers, delimited by '|'

An analytics or affiliate-tracking system can use these variables as part of their tracking-pixel or other callback notification by simply referencing these variables in their callback/tracking code.  

Advanced tip: If passing product ID/model numbers needs a different delimiter in your system, simply do a replacement on it while doing your output, such as: 

```
str_replace('|', '@', $order_summary['products_ordered_models']);
```
if you wanted to replace `|` with `@`, for example.


Value to replace | What to replace it with
-----------------|------------------------
Order Number|`<?php echo $order_summary['order_number']; ?>`
Subtotal|`<?php echo $order_summary['order_subtotal']; ?>`
Amount of credits/discounts on the order|`<?php echo $order_summary['credits_applied']; ?>`
Final Total|`<?php echo $order_summary['order_total']; ?>`
Commissionable Order Amount (does not include discounts)|`<?php echo $order_summary['commissionable_order']; ?>`
Commissionable amount, formatted per currently selected currency formatting rules set in your admin|`<?php echo $order_summary['commissionable_order_formatted']; ?>`
Coupon Code, if any (often used for referral tracking)|`<?php echo $order_summary['coupon_code']; ?>`
Currency Code (3-letter ISO code)|`<?php echo $order_summary['currency_code']; ?>`
Exchange Rate applied, if any|`<?php echo $order_summary['currency_value']; ?>`
Payment Module used|`<?php echo $order_summary['payment_module_code']; ?>`
Shipping Method selected by customer|`<?php echo $order_summary['shipping_method']; ?>`
Order Status (number) denoting the order's status in your store at this present time.|`<?php echo $order_summary['orders_status']; ?>`
Tax on the order|`<?php echo $order_summary['tax']; ?>`
Shipping Cost on the order|`<?php echo $order_summary['shipping']; ?>`
Order Total (the final/net total of the order, the amount sent for payment)|`<?php echo $order_summary['order_total']; ?>`
Product Model Numbers (delimited with '`\|`')|`<?php echo $order_summary['products_ordered_models']; ?>`
Product IDs (delimited with '`\|`')|`<?php echo $order_summary['products_ordered_ids']; ?>`


## Examples:  

### Snap Affiliates
No need to edit any core Zen Cart files.  
Use the plugin [Snap Affiliates](https://www.zen-cart.com/downloads.php?do=file&id=1635). 

### iDevAffiliate  
No need to edit any core Zen Cart files.  
Simply create a new file: `/includes/modules/pages/checkout_success/jscript_idevaffiliate.php` and be sure to set the correct URL for your iDevAffiliate system, and appropriate profile number:

```
<?php
  echo '<script type="text/javascript" src="http://www.yourdomain.com/idevaffiliate/sale.php?profile=1&idev_saleamt=' . $order_summary['commissionable_order_formatted'] . 
       '&idev_ordernum=' . $order_summary['order_number'] . '&products_purchased=' . $order_summary['products_ordered_models'] . '&coupon_code=' . urlencode($order_summary['coupon_code']) .
       '"></script>';
```

or use an image pixel instead, by adding it to your tpl_footer.php:

```
if ($current_page_base == 'checkout_success') {
    echo '<img border="0" src="http://www.yoursite.com/idevaffiliate/sale.php?profile=1&idev_saleamt=' . $order_summary['commissionable_order'] . '&idev_ordernum=' . $order_summary['order_number'] . '&coupon_code=' . $order_summary['coupon_code'] . '&products_purchased=' . $order_summary['products_ordered_ids'] . '" height="1" width="1">';
} 
```

### JROX JAM  

**Note: As late 2022, it appears that JROX JAM is no longer actively supported.  Migrating to an alternative is recommended.**

No need to edit any core Zen Cart files.  
Simply create a new file: `/includes/modules/pages/checkout_success/jscript_jam.php` and be sure to set the correct URL for your JAM system:

```
<?php
   echo '<script type="text/javascript"  src="https://www.YOURDOMAIN.com/affiliates/sale.php?amount=' . $order_summary['commissionable_order'] . '&trans_id=' . $order_summary['order_number'] . '"></script>';
```

**Adding product IDs or Model Numbers on older versions:**  

Add the following extra code before the tracking pixel/script code above if you want to have product ID or Model data available:

```
if (!isset($order_summary['products_ordered_models'])) {
  $products_array = array();
  $products_query = "SELECT products_id, products_model
                     FROM " . TABLE_ORDERS_PRODUCTS . "
                     WHERE orders_id = :ordersID
                     ORDER BY products_id";
  $products_query = $db-&gt;bindVars($products_query, ':ordersID', $orders_id, 'integer');
  $products = $db-&gt;Execute($products_query);
  while (!$products-&gt;EOF) {
    $products_array[urlencode($products-&gt;fields['products_id'])] = urlencode($products->fields['products_model']);
    $products-&gt;MoveNext();
  }
  $order_summary['products_ordered_ids'] = implode('|', array_keys($products_array));
  $order_summary['products_ordered_models'] = implode('|', array_values($products_array));
}
```


## Advanced Use  
Advanced programmers might choose programmatic hooks instead of JavaScript callbacks, by invoking the [notifier system](/dev/code/notifiers/). This involves hooking 
`NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES` and referencing the 
`$_SESSION['order_summary']` array in place of the non-global 
`$order_summary` array.  

This could allow a bespoke tracking service to be invoked without needing to force extra activities down to the customer's browser.  

Related article: [Adding a tracking pixel](/user/template/tracking_pixel/).
