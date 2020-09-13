---
title: Building a Home Page widget
description: Adding information to the admin dashboard 
category: code
weight: 10
type: codepage
---

Creating a widget of your own is just a matter of modifying `admin/index_dashboard.php` and adding in your logic.  For example, one store wanted to monitor orders in a specific status, and make them visible on the home page.  Here's what they did: 

```
    <div class="reportBox">
        <div class="header"><?php echo "Held Orders"; ?> </div>
        <?php  $orders = $db->Execute("SELECT o.orders_id AS orders_id, o.customers_name AS customers_name, o.date_purchased AS date_purchased, ot.text AS order_total FROM " . TABLE_ORDERS . " o LEFT JOIN " . TABLE_ORDERS_TOTAL . " ot ON (o.orders_id = ot.orders_id and class = 'ot_total') WHERE orders_status = 7 ORDER BY orders_id DESC");

        if ($orders->EOF) {
          echo '              <div class="row">No Held Orders</div>' . "\n"; 
        } else { 
          while (!$orders->EOF) {
            echo '              <div class="row"><span class="left"><a href="' . zen_href_link(FILENAME_ORDERS, 'oID=' . $orders->fields['orders_id'] . '&action=edit&origin=' . FILENAME_DEFAULT, 'NONSSL') . '" class="contentlink"> ' . $orders->fields['customers_name'] . '</a></span><span class="center">' . $orders->fields['order_total'] . '</span><span class="right">' . "\n";
            echo zen_date_short($orders->fields['date_purchased']);
            echo '              </span></div>' . "\n";
            $orders->MoveNext();
          }
        }
        ?>
    </div>
```

A plugin called [Orders in Status Dashboard Widget](https://www.zen-cart.com/downloads.php?do=file&id=2284) can be used to build something similar for your site. 

