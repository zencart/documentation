---
title: Shipping Problems 
description: Problems with calculating a shipping rate 
category: troubleshooting
weight: 10
---

---

### My shipping is figured wrong, it is 3 pounds too heavy
Any shipping module that uses weight for the calculations also takes into account a built-in Tare weight.
The Tare setting (configurable in your store Admin) adds extra weight to compensate for packaging materials.

To change the Tare, go to 
[Admin > Configuration > Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging/)
You will be able to change the Tare on this screen.

You can set either and/or both a percentage or weight for Tare and Large Package.

Entered as percentage:weight

**Examples:**
```
Disabled completely = 0:0
10% + 1lb = 10:1
0% +3lb = 0:3
5% + 0lbs = 5:0
```

This way both the Tare for small to medium packages has a flexible option of percentage + weight and the Large Package increase has an option of a percentage + weight.

---

### Sorry, we are not shipping to your region at this time.
This message usually occurs when you have no available shipping modules for that customer's address.

A module is unavailable for one of two reasons:
it's not installed
or it's installed but has a Shipping Zone restriction set on it, and the customer's shipping address isn't in that specified zone.


Or maybe the order qualifies for Free Shipping, but you don't have the freeshipper module installed.

--- 

### The USPS module is returning an error when I try to checkout

If you are receiving this error:

```
An error occurred with the USPS shipping calculations. If you prefer to use USPS as your shipping method, please contact the store owner.
```

You need to call or email USPS and have them move your account to the production server.

See [USPS](/user/shipping/usps/).

