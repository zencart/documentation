---
title: Downloadable Products - can they also be shippable? 
description: Configuring Zen Cart Combo Products 
category: products
weight: 10
---

In addition to physical products and downloadable products, you may define _combo_ products that have a downloadable component and a physical component. 

Let's review the rules for configuration of physical and downloadable products. 

## Physical Products 
Do you use Always Free Shipping or 0 weight to mean Free Shipping?  

If so, go to Configuration > Shipping/Packaging and check the setting 

```
Order Free Shipping 0 Weight Status  
If there is no weight to the order, does the order have Free Shipping?  
0= no  
1= yes  

**Note:** When using Free Shipping, enable the Free Shipping Module (freeshipper).  It will only show when shipping is free.
```

## Downloadable Products 

Downloads are NOT set to Virtual Product and NOT set to Always Free Shipping.  They are already "recognized" as Free shipping by virtue of the Download filename on the Attributes. See [Important Facts about Download Settings](/user/products/downloadable/#important-facts-about-download-settings). 

Check the settings are:  

<pre>
Product is Virtual: **No, Shipping Address Required**

Always Free Shipping: **No, Normal Shipping Rules**</td>
</pre>

If a Download Product has either of those settings set any other way, then shipping costs may not be calculated correctly.

## Combo Products 
As noted above, a Combo Product is a product that is BOTH a Download and a Physical Product ALWAYS.

This is different than a Product that is a Download OR a Physical Product such as a Media Product that you sell as:  

<pre>
Download MP3  
-- or --  
Send me a CD  
</pre>

A Product that is a Download OR a Physical Product, is setup like a normal product and just the Attribute with the filename is used for the Download.  The Weight may be put on the Attribute for the Physical Product, or the Weight may put on the Product itself with a negative weight on the Attribute with the Download.

I prefer that the Attribute hold the Weight. 

**NOTE:** Attribute Weight can be turned off in the Catalog > Product Type > EDIT LAYOUT. 

This Product gets the Weight added to the Product and/or the Attribute.

The Product is marked as:  

<pre>
Product is Virtual: **No, Shipping Address Required**

Always Free Shipping: **Special, Product/Download Combo Requires a Shipping Address**

</pre>

The Special, Product/Download Combo knows that the Weight counts in a Normal shipping manner and that the Download on the Attribute works in a Normal download manner.  This lets shipping work properly, despite the Download for shipping my Item Count, Price or Weight. 

Just setup the Product with the Special, Product/Download Combo and put the weight on the Product and/or Attribute(s) for shipping, and add the Download to the Attribute(s) as needed. 

