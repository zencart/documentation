---
title: Tax configuration in the United States
description: Calculating taxes in the USA 
category: taxes
aliases: 
    - /user/localization/us_taxes
    - /user/locations/us_taxes
weight: 10
---

This advice should work for state with a single rate of sales tax.

FIRST, set your store's zone properly:  
**Admin > Configuration > My Store > Zone**  
Choose your country and zone from the lists provided by the edit button.  

Here is an example, for setting up taxes for the state of Colorado:  

Go to:

**Admin > Locations/Taxes > Zones Definitions > Insert**

Zone Name: Colorado  
Description: Colorado State Sales Tax (or whatever you like)  
click on 'insert'  

Click on 'Details' after creating a zone  
Click on 'Insert'  
Country = United States  
Zone = Colorado  
Click on 'insert'  

Go to:  
**Admin > Locations/Taxes > Tax Classes**

Click on 'New Tax Class'  
Title = Taxable Goods  
Description = Whatever you like  
Click on 'insert'  

Go to:  
**Admin > Locations/Taxes > Tax Rates**  

Click on 'New Tax Rate'  
Select your zone, 'Colorado'  
Set your tax rate  
give it a description, ex: Colorado State Sales Tax  
Click on insert  

Last, make sure you apply the new tax class that you created (Taxable Goods) to any and all products that you might be charging tax on.  

To make this faster when adding new products, in the Admin area, you can select a default Tax Class to be applied to all new products you create.  
Go to [Admin > Catalog > Product Types](/user/admin_pages/catalog/product_types/), then choose a product type (likely `Product - General`), and click
*Edit Layout*, then  *Default Tax Class*.

