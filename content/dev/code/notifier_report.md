---
title: Notifier Report 
description: Zen Cart Notifier Report
category: code
type: codepage
weight: 10
---

<!-- RELEASETIME - update -->


<!-- content here --> 

**UNDER CONSTRUCTION**

File: ipn_main_handler.php

```
line#305: $zco_notifier->notify('NOTIFY_CHECKOUT_PROCESS_BEFORE_ORDER_TOTALS_PROCESS');
line#307: $zco_notifier->notify('NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_TOTALS_PROCESS');
line#319: $zco_notifier->notify('NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE');
line#326: $zco_notifier->notify('NOTIFY_CHECKOUT_PROCESS_AFTER_PAYMENT_MODULES_AFTER_ORDER_CREATE');
line#361: $zco_notifier->notify('NOTIFY_CHECKOUT_PROCESS_AFTER_ORDER_CREATE_ADD_PRODUCTS');
line#364: $zco_notifier->notify('NOTIFY_CHECKOUT_PROCESS_AFTER_SEND_ORDER_EMAIL');
line#398: $zco_notifier->notify('NOTIFY_CHECKOUT_PROCESS_HANDLE_AFFILIATES', 'paypalipn');
line#479: $zco_notifier->notify('NOTIFY_PAYPALIPN_STATUS_HISTORY_UPDATE', array($ordersID, $new_status, $txn_type));
```

