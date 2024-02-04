---
title: Attribute Pricing 
description: How to use Zen Cart Attributes to set product pricing
category: products
weight: 10
---

### Product Priced by Attributes vs Attributes with Prices 
The Zen Cart [product editing page](/user/products/product_edit/) has a field called _Product Priced by Attributes_.  This field controls how product prices are displayed on the product info page.  When *Product Priced by Attributes*  is set to Yes, the product prices include the attribute price.  When it is set to no, the prices are shown as increments on top of the product price.

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

- Pricing by Word or Letter - Both of these options are available for attributes with option type TEXT. 

### Attribute Quantity Discounting vs Product Quantity Discounting

If you only want to discount a specific variant of a product, with a specific attribute setting, attribute quantity discounting is the solution.  

Suppose you want to charge $10 for size XL shirts.  To do this, you would go to Attributes Controller, edit the attribute XL, and set the Price field, under Prices and Weights, to 10. 

Now suppose you want to change the pricing for XL shirts, so that you charge $10 for purchases of 1-4, but quantities of 5 or more, you only charge $3.  Remove the Price setting of 10, and enter the following in Attributes Qty Price Discount: 

4:10,5:3

This field is on the lower left hand side of the Attributes Controller page, below One Time Factor and above Attribute Flags. 

![Attribute Quantity Discounts](/images/attr_qd.png)

This is an example of [colon separated pairs configuration](/user/running/colon-separated-pairs/) which is common in Zen Cart.  In this case, this setting is read, "for quantities of up to 4, add $10 to the price; for quantities of 5 or more, add 3 to the price." 

**Note:** Don't confuse attribute discounts with [product quantity discounts](/user/products/quantity_discounts/), which are set using [Products Price Manager](/user/admin_pages/catalog/products_price_manager/). Product Quantity Discounting discounts bulk purchases of a specific product, irrespective of how its attributes are set.   
