---
title: Shipping Calculations 
description: Weight, tare and shipping rates
category: shipping
weight: 10
---

To view the settings related to shipping, go to 
[Admin > Configuration > Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging/). 

There is no support for dimensional calculations in the Zen Cart shipping calculations; it is done entirely by weight. There are some Plugins that handle dimensions if you need that capability, and dimensions for products are supported starting in Zen Cart 2.0.0; see [shipping dimensions](/user/shipping/dimensions).

The "small to medium box" corresponds to "an order whose weight does not exceed the maximum package weight." 

* If the weight of all the products in the order is less than or equal to the setting in _Enter the Maximum Package Weight you will ship_, 
then the order is assumed to fit in a small/medium box.  
The weight of the package will be grossed up by _Package Tare Small to Medium  - added percentage:weight_, 
and this weight will be passed to the shipping modules for your cart, to prepare quotes.
* If the weight of all the products in the order is greater than the setting in _Enter the Maximum Package Weight you will ship_, 
the weight of the package will be grossed up by _Larger packages - added packaging percentage:weight_, 
and that weight will be passed to the shipping modules for your cart, to prepare quotes. 
* The _number of boxes_ calculated by the shipping module does *not* take into account that products generally cannot be split into "equal parts" to meet weight restrictions.
For this reason most shopowners will choose not to display this value (i.e. they will set _Display Number of Boxes and Weight Status_ to either 0 or 2). 


## Tare
Tare weight is the additional weight of the box, including any protective materials such as foam or wrap, 
and all the other things that add to the weight of your final shipment,
over and above the weight of the product(s). 

On [Admin > Configuration > Shipping/Packaging](/user/admin_pages/configuration/configuration_shippingpackaging/), you can set the tare for small to medium sized packages and for large packages. 

The tare is entered as a percentage increase, followed  by a colon, followed by a flat increase.
So `10:1` means a `10% increase over the weight of the product plus 1 pound`,
and 
`0:0.5` means a `an increase of half a pound over the weight of the product`.

Consider a 5 lb product which fits in a small box with a tare setting of `10:1`. 
This means the final weight of the package, which will be passed to shipping modules, 
is `5 lbs + 10% of 5 pounds + 1 pound`, or `6.5 pounds`.

## Package Size 
The first tare value, which is called *Package Tare Small to Medium*, is used
for shipments whose product weight is less or equal to the value you entered for 
*Enter the Maximum Package Weight you will ship*.  

So if your maximum weight is 60 pounds, an order whose product weight is 
60 pounds or less will be increased by the tare settings in *Package Tare Small to Medium*. 

If your maximum weight is 60 pounds and the product weight of an order is over 60 pounds, 
the weight will be increased by the value of *Larger packages - added packaging percentage:weight*, 
and quotes prepared as though the order is being shipped in multiple boxes (each of which will weigh 60 pounds or less). 

## Examples 
In these examples the following short forms will be used for configuration values: 

- "Maximum Weight" - "Enter the Maximum Package Weight you will ship"
- "Small Tare" - "Package Tare Small to Medium - added percentage:weight"
- "Large Tare" - "Larger packages - added packaging percentage:weight" 


### Example 1 (Max weight 60 lbs, order weight < 60 lbs)

- Settings: Maximum Weight = 60 pounds, both tare settings 10:1. 
- Order: 3 products each weighing 15 pounds 

Zen Cart will return these values: 

- number of boxes = 1
- total weight: 50.5 lbs 

Calculation of total weight: 45 pounds of product, grossed up by 10% = 49.5 pounds, plus 1 pound = 50.5 pounds. 


### Example 2 (Max weight 60 lbs, order weight > 60 lbs)

- Settings: Maximum Weight = 60 pounds, both tare settings 10:1. 
- Order: 5 products each weighing 15 pounds 

Zen Cart will return these values: 

- number of boxes = 2 _(*)_
- total weight: 83.5 lbs 

_(*) Note that the number of boxes might not be accurate: if you use 2 boxes, one will be heavier than the other since each of 5 items is 15 lbs._

Calculation of total weight: 75 pounds of product, grossed up by 10% = 82.5 pounds, plus 1 pound = 83.5 pounds. 


### Example 3 (Max weight 15 lbs, order weight < 15 lbs)

- Settings: Maximum Weight = 15 pounds, both tare settings 10:1. 
- Order: 2 products each weighing 5 pounds 

Zen Cart will return these values: 

- number of boxes = 1
- total weight: 12 lbs 

Calculation of total weight: 10 pounds of product, grossed up by 10% = 11 pounds, plus 1 pound = 12 pounds. 


### Example 4 (Max weight: 15 lbs, order weight > 15 lbs, tares same)

- Settings: Maximum Weight = 15 pounds, both tare settings 10:1 

- Order: 3 products each weighing 10 pounds 

Zen Cart will return these values: 
 
- number of boxes = 2 _(*)_
- total weight: 34 lbs  

_(*) Note that the number of boxes is misleading because a product cannot be split in half; you will really need 3 boxes._

Calculation of total weight: 30 pounds of product, grossed up by 10% = 33 pounds, plus 1 pound = 34 pounds. 


### Example 5 (Max weight: 15 lbs, order weight > 15 lbs, tares differ)

- Settings: Maximum Weight = 15 pounds, small tare setting 10:1, large tare setting 10:5 

- Order: 3 products each weighing 10 pounds 

Zen Cart will return these values: 
 
- number of boxes = 2 _(*)_
- total weight: 38 lbs  

_(*) See note in examples above_

Calculation of total weight: 30 pounds of product, grossed up by 10% = 33 pounds, plus 5 pounds = 38 pounds. 

### Products which Ship in their Own Boxes 

Since Zen Cart 2.0.0, it has been possible to identify products which ship in their own boxes using the new [shipping dimensions](/user/shipping/shipping_dimensions/) settings.   Such products will not incur additional tare weight; the weight entered in their `Products Shipping Weight` field will cover the entire weight. 
