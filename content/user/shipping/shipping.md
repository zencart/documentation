---
title: About Shipping Modules
description: How can I ship orders?
category: shipping
weight: 1
---

Shipping modules allow you to charge your customers for delivery.

## How Shipping Rates Are Quoted

By default, most shipping modules prepare quotes based on weight and destination.

### Determining Weight

Zen Cart takes the items in your shopping cart and looks at the product details you've configured for them -- particularly the weight. 

It uses that information to assemble a list of all the packages that need to be shipped. By default it uses a very simplified calculation of "how much do all the products weigh?" and then "how many boxes must be used, based on max weight per package?". It also incorporates a "tare" amount (packaging materials weight) for each package. See [How Weight and Tare Are Determined](/user/shipping/shipping_calculations/) for more details.

Then it takes those packages and lets each active shipping module determine available rates.


### What is Transmitted To Carriers?
Several basic shipping modules that are based on defined rates for defined zones (both defined by the storeowner) don't transmit anything to anyone.

Modules that are configured to get real-time quotes from carriers will transmit the following information to the carrier's quoting service:

  - store's zip/postal code
  - customer's zip/postal code
  - number of packages
  - weight of each package
  - some modules might transmit package dimensions if the module supports this feature

### How To Use Shipping Rate Selected By Customer

At checkout the customer chooses from the available shipping options presented. Their choice is stored in their order as the description of the "shipping" subtotal.

Then when you have packaged up the order and take it to the carrier you tell the person at the counter what Service the customer selected, and you pay them to ship it.


## Applying Shipping Restrictions To Modules

Many shipping modules may be restricted so that they only work in specific zones - an existing one, or one you have created.  

To learn how to create a new zone, see [creating zone definitions](/user/locations/zone_definitions/). 


## Available Shipping Modules

The list of available shipping modules may be seen by going to [Admin > Modules > Shipping](/user/admin_pages/modules/shipping/).

Zen Cart has a number of built-in shipping modules which allow you to charge for shipping based on various factors in the order: 

- Flat - Charge a single flat rate on all shipments
- Item - Charge per item
- [Zones](/user/shipping/zones/) - Charge different rates for delivering to different zones 
- [Table](/user/shipping/table/) - Charge according to a table of rates based on weight, item count or item price, entered as [colon-separated pairs](/user/running/colon-separated-pairs/). 

Zen Cart also integrates with a number of shipping vendors using plugins:

- [UPS](/user/shipping/ups/)
- [USPS](/user/shipping/usps)
- [FedEx](/user/shipping/fedex)
- [Canada Post](https://www.zen-cart.com/downloads.php?do=file&id=4)
- [Royal Mail](https://www.zen-cart.com/downloads.php?do=file&id=190)

More shipping plugins may be found in the [Shipping module section of the Plugins Library](https://www.zen-cart.com/downloads.php?do=cat&id=11).


## Considering Developing A Shipping Module?

Developers wishing to create a shipping module should see the [dev FAQs on modules](/dev/code/modules/). 
