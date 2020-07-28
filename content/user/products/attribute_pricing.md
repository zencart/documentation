---
title: Attribute Pricing 
description: How to use Zen Cart Attributes to set product pricing
category: products
weight: 10
---

### Product Priced by Attributes vs Attributes with Prices 
The Zen Cart product editing page has a field called [Product Priced by Attributes](user/admin_pages/catalog/categories_products/).  This field controls how product prices are displayed on the product info page.  When *Product Priced by Attributes*  is set to Yes, the product prices include the attribute price.  When it is set to no, the prices are shown as increments on top of the product price.

Consider a shirt which is $20 for sizes S-L, but an extra $10 for XL and an extra $20 for XXL. 

With *Product Priced by Attributes* = No, the prices would look like this:

<pre>
Products Price $20
S-L
XL (+$10)
XXL (+$20) 
</pre>

With *Product Priced by Attributes* = Yes, the prices would look like this:

Products Price starting at $20

<pre>
S-L ($20) 
XL ($30)
XXL ($40) 
</pre>

## Settings in Attributes Controller 

Using the [Attributes Controller](/user/admin_pages/catalog/attributes_controller/) you can adjust attribute prices in a number of ways. 

![Prices and Weights](/images/attributes_controller_prices.png) 

- Entering a value in the *Price* field will increase the price by the specified value.  A decrease ("-") option is also available to lower the price. 

- Entering a value in the *One Time* field will increment the cost of the product in the cart by that amount, but only one time no matter how many of that product are purchased.

- OFFSET/ONETIME OFFSET - FIXME  

- An attribute may be subject to quantity discounting using the fields *Attributes Qty Price Discount* and *Onetime Attributes Qty Price Discount*.   These settings are configured using [colon-separated pairs](/user/running/colon-separated-pairs/). 

- Pricing by Word or Letter - Both of these options are available for attributes with option type Text. 

