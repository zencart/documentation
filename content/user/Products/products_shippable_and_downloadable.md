---
title: Products - can they be both downloadable and shippable? 
category: products
weight: 1
---

You have Products, Downloads and some Combo Products ...  

First, let's make sure that you have Products setup correctly ...  

Do you use Always Free Shipping or 0 weight to mean Free Shipping?  

If so, go to Configuration -> Shipping/Packaging and check the settings 

```
Order Free Shipping 0 Weight Status  
If there is no weight to the order, does the order have Free Shipping?  
0= no  
1= yes  

Note: When using Free Shipping, Enable the Free Shipping Module this will only show when shipping is free.
```

NOTE: the Free Shipping module that is referenced here is called the FREE SHIPPING! freeshipper shipping module 

Next, let's look at a Download Product, one that is ONLY a Download

Downloads are NOT set to Virtual Product and NOT set to Always Free Shipping ... they are already "recognized" as Free shipping by virtue of the Download filename on the Attributes ...  

Check the settings are:  

<div style="margin: 5px 20px 20px;">

<div style="margin-bottom: 2px;" class="smallfont">Quote:</div>

<table width="100%" cellspacing="0" cellpadding="5" border="0">

<tbody>

<tr>

<td style="border: 1px inset ;" class="alt2">Product is Virtual: **No, Shipping Address Required**</td>

</tr>

</tbody>

</table>

</div>

<div style="margin: 5px 20px 20px;">

<div style="margin-bottom: 2px;" class="smallfont">Quote:</div>

<table width="100%" cellspacing="0" cellpadding="5" border="0">

<tbody>

<tr>

<td style="border: 1px inset ;" class="alt2">Always Free Shipping: **No, Normal Shipping Rules**</td>

</tr>

</tbody>

</table>

</div>

If a Download Product has either of those settings set any other way, then they count for 2 Products not to be shipped and can mess up shipping costs, especially for Shipping based on Price or Item Count ...  

Then, there is the Combo Product ... a Product that is BOTH a Download and a Physical Product ALWAYS ...  

This is different than a Product that is a Download OR a Physical Product such as a Media Product that you sell as:  
Download MP3  
-- or --  
Send me a CD  

A Product that is a Download OR a Physical Product, is setup like a Normal Product and just the Attribute with the filename is used for the Download ... and the Weight can be put on the Attribute for the Physical Product OR ... the Weight is put on the Product itself with a negative weight on the Attribute with the Download ...  

I prefer that the Attribute hold the Weight or the Download so the Product does not look moofy with a Negative weight on the Attribute ...  

NOTE: Attribute Weight can be turned off in the Catalog -> Product Type -> EDIT LAYOUT ...  

Now, back to the Combo Product which is BOTH a Physical Product and a Download at the SAME time ...  

This Product gets the Weight added to the Product and/or the Attribute ...  

The Product is marked as:  

<div style="margin: 5px 20px 20px;">

<div style="margin-bottom: 2px;" class="smallfont">Quote:</div>

<table width="100%" cellspacing="0" cellpadding="5" border="0">

<tbody>

<tr>

<td style="border: 1px inset ;" class="alt2">Product is Virtual: **No, Shipping Address Required**</td>

</tr>

</tbody>

</table>

</div>

<div style="margin: 5px 20px 20px;">

<div style="margin-bottom: 2px;" class="smallfont">Quote:</div>

<table width="100%" cellspacing="0" cellpadding="5" border="0">

<tbody>

<tr>

<td style="border: 1px inset ;" class="alt2">Always Free Shipping: **Special, Product/Download Combo Requires a Shipping Address**</td>

</tr>

</tbody>

</table>

</div>

The Special, Product/Download Combo knows that the Weight counts in a Normal shipping manner and that the Download on the Attribute works in a Normal download manner ... this lets shipping work properly, despite the Download for shipping my Item Count, Price or Weight ...  

Just setup the Product with the Special, Product/Download Combo and put the weight on the Product and/or Attribute(s) for shipping ... and add the Download to the Attribute(s) as needed ...  


