---
title: Shipping Calculations 
description: Zen Cart Shipping Calculations 
category: shipping
weight: 1
---

To view the settings related to shipping, go to 
[Admin > Configuration > Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging/). 

There is no support for dimensional calculations in the Zen Cart shipping calculations; it is done entirely by weight.  The "small to medium box" corresponds 
to "an order whose weight does not exceed the maximum package weight." 

* If the weight of all the products in the order is less than or equal to the setting in 
_Enter the Maximum Package Weight you will ship_, then the order
is assumed to fit in a small/medium box.  The weight of the package
will be grossed up by _Package Tare Small to Medium  - added percentage:weight_, and this weight will be passed to the shipping modules for your cart. 
* If the weight of all the products in the order is greater than the setting in _Enter the Maximum Package Weight you will ship_, the 
weight of the package will be grossed up by _Larger packages - added packaging percentage:weight_, and that weight will be passed to the shipping mdules for your cart. 
* The _number of boxes_ calculated by the shipping module does not take into account that products generally cannot be split into parts to meet weight restrictions.  For this reason, most shopowners will choose not to display this value (i.e. they will set _Display Number of Boxes and Weight Status_ to either 0 or 2). 


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
for shipments whose product weight is less or equal to than the value you entered for 
*Enter the Maximum Package Weight you will ship*.  

So if your maximum weight is 60 pounds, an order whose product weight is 
60 pounds or less will be increased by the tare settings in *Package Tare Small to Medium*. 

If your maximum weight is 60 pounds and the product weight of an order is over 60 pounds, the weight will be increased by the value of *Larger packages - added packaging percentage:weight*, and shipped in multiple boxes (each of which will weigh 60 pounds or less). 

## Examples 
In these examples the following short forms will be used for configuration values: 

- "Maximum Weight" - "Enter the Maximum Package Weight you will ship"
- "Small Tare" - "Package Tare Small to Medium - added percentage:weight"
- "Large Tare" - "Larger packages - added packaging percentage:weight" 

### Example 1 

- Settings: Maximum Weight = 15 pounds, both tare settings 10:1. 
- Order: 2 products each weighing 5 pounds 

Zen Cart will return these values: 

- number of boxes = 1
- total weight: 12 lbs 

Calculation of total weight: 10 pounds of product, grossed up by 10% = 11 pounds, plus 1 pound = 12 pounds. 


### Example 2  

- Settings: Maximum Weight = 15 pounds, both tare settings 10:1 

- Order: 3 products each weighing 10 pounds 

Zen Cart will return these values: 
 
- number of boxes = 2 (*) 
- total weight: 34 lbs  

(*) Note that the number of boxes is misleading because a product cannot be split in half; you will really need 3 boxes. 

Calculation of total weight: 30 pounds of product, grossed up by 10% = 33 pounds, plus 1 pound = 34 pounds. 

### Example 3 

- Settings: Maximum Weight = 15 pounds, small tare setting 10:1, large tare setting 10:5 

- Order: 3 products each weighing 10 pounds 

Zen Cart will return these values: 
 
- number of boxes = 2 (*) 
- total weight: 38 lbs  

(*) See note in example 2 

Calculation of total weight: 30 pounds of product, grossed up by 10% = 33 pounds, plus 5 pounds = 38 pounds. 



