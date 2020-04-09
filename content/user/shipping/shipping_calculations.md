---
title: Shipping Calculations 
description: Zen Cart Shipping Calculations 
category: shipping
weight: 1
---

### Tare
Tare weight is the additional weight of the box, any protective materials such as foam or wrap, and all the other things that add to the weight of your final shipment,
over and above the weight of the product(s). 

On [Admin > Configuration > Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging/), you can set the tare for small to medium sized packages and for large packages. 

The tare is entered as a percentage increase, followed  by a colon, followed by a flat increase.   So 10:1 means a 10% increase over the weight of the product plus 1 pound.

Consider a 5 lb product which fits in a small box with a tare setting of 10:1. 
This means the final weight of the package, which will be passed to shipping modules, 
is 5 lbs + 10% of 5 pounds + 1 pound, or 6.5 pounds.

## Package Size 
The first tare value, which is called *Package Tare Small to Medium*, is used
for shipments whose product weight is less than the value you entered for 
*Enter the Maximum Package Weight you will ship*.  

So if your maximum weight is 60 pounds, an order whose product weight is 
less than this will be increased by the tare settings in *Package Tare Small to Medium*. 

If your maximum weight is 60 pounds and the product weight of an order is over 60 pounds, the weight will be increased by the value of *Larger packages - added packaging percentage:weight*, and shipped in multiple boxes (each of which will weigh 60 pounds or less). 

