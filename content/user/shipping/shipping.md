---
title: About Shipping Modules
description: How can I ship orders?
category: shipping
weight: 1
---

Shipping modules allow you to charge your customers for delivery.

The list of available shipping modules may be seen by going to [Admin > Modules > Shipping](/user/admin_pages/modules/shipping/).

Zen Cart has a number of built-in shipping modules which allow you to charge for shipping based on various factors in the order: 

- Flat - Charge a single flat rate on all shipments
- Item - Charge per item
- Zones - Charge different rates for delivering to different zones 
- Table - Charge according to a table of rates based on weight, item count or item price, entered as [colon-separated pairs](/user/running/colon-separated-pairs/). 

Zen Cart also integrates with a number of shipping vendors using plugins:

- [UPS](https://www.zen-cart.com/downloads.php?do=file&id=1293)
- [UPS XML with Negotiated Rates](https://www.zen-cart.com/downloads.php?do=file&id=126)
- [USPS](https://www.zen-cart.com/downloads.php?do=file&id=1292)
- [Canada Post](https://www.zen-cart.com/downloads.php?do=file&id=4)
- [Royal Mail](https://www.zen-cart.com/downloads.php?do=file&id=190)

More shipping plugins may be found in the [Shipping module section of the Plugins Library](https://www.zen-cart.com/downloads.php?do=cat&id=11).

Many shipping modules may be restricted so that they only work in specific zones - an existing one, or one you have created.  To learn how to create a new zone, see [creating zone definitions](/user/locations/zone_definitions/). 

Developers wishing to create a shipping module should see the [dev FAQs on modules](/dev/code/modules/). 
