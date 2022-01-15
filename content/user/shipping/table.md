---
title: Table Rate Shipping Module Setup 
description: How to price shipping by item weight, price or count
category: shipping 
weight: 10
---

The Table Rate Shipping module allows you to price your shipping in any one of three possible ways: 

- according to the total weight of the shipment
- according to the total price of the shipment
- according to the number of items in the shipment.

The rate table is specified as a series of [colon-separated pairs](/user/running/colon-separated-pairs/).   For example, you might want an order than weighs more than 0 and less than or equal to 3 to cost 5.50 to ship. 

You would use the following setting for Shipping Table: 
```
3:5.5
```

