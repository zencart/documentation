---
title: Tax configuration in Canada 
description: Calculating taxes in Canada 
category: taxes 
aliases: 
    - /user/localization/canada_taxes
    - /user/locations/canada_taxes
weight: 10
---

Vendors operating in Canada need to accommodate numerous tax configurations to support proper tax collection on sales to customers in provinces where they are registered to sell. There's a Federal GST, HST, and provincial PST/RST.  

Tax Zones / Rates configuration can be a little confusing at times, as the terms are easily and accidentally swapped. 

Hopefully this short article will help clarify.  

**=========================  
Understanding Terminology  
=========================**  
TAX CLASS = A setting assigned to PRODUCTS and to SHIPPING that's used to calculate final taxes.  
TAX ZONE = A regional setting used to help determine tax rates by geography.  
TAX RATE = A rate calculated by combining a product's tax class and shipping zone with the relevant tax percentage.  

Zen Cart uses SHIPPING ADDRESS to determine appropriate taxes, i.e. which TAX ZONE you are shipping into. **NOTE:** this is the shipping address, and *NOT* the billing address.  

A TAX RATE is determined by comparing SHIPPING ADDRESS to the Tax ZONE set up for the TAX RATE; and also by Tax Class assigned to each product.  

You can only assign ONE TAX CLASS to a product.  
In many stores, you will only have one TAX CLASS (GST/HST/PST) since all goods are either taxable or non-taxable.  
When would you use different rates? One example would be if, say, CLOTHES were taxed at a different rate than BOOKS which are in turn different from DVDs. You could create a different TAX CLASS for each family ("class") of product in that case.  

In the following examples, we will be dealing with only ONE tax CLASS for products.  
You likely want the GST for SHIPPING to show up separately, so we will make a separate "TAX CLASS" for "GST on Shipping".  

**========= PROBLEMS: =========**  

The method below shows the GST and PST totaled together on the same line (see sample output below).  

Having said that, the only problem is that the two taxes are summed together onto one line.  
However, the GST number is displayed, and the percentages (rates) used are displayed, and nothing is hidden, so I believe that this will be acceptable according to Federal & Provincial Gov't requirements (but I AM NOT AN ACCOUNTANT!!!!).  

Best part is: IT DOESN'T REQUIRE ANY CONTRIBUTIONS!!!!! Just a careful setup of the zones.  

**===================  
Step-by-Step SETUP:  
===================**  

STEP (1): Set the location for your store:  

Configuration > My Store  

- Country: Canada  
- Zone: Ontario  

STEP (2): Create the "Tax Zones". The are geographical regions where a particular set of tax laws applies  
Locations/Taxes > Zones Definitions  

Create the Zone for all of Canada  

- Zone Name: Canada GST Zone  
- Description: GST (except Eastern Canada: NS, NB, NL)  

Now click on the newly created "Canada GST Zone" row to drill down one level to "Sub Zones"  
Click INSERT to create 10 new sub-zones, one at a time:  

- Country: Canada; Zone: Alberta  
- Country: Canada; Zone: British Columbia  
- Country: Canada; Zone: Manitoba  
- Country: Canada; Zone: Northwest Territories  
- Country: Canada; Zone: Nunavut  
- Country: Canada; Zone: Ontario  
- Country: Canada; Zone: Prince Edward Island  
- Country: Canada; Zone: Quebec  
- Country: Canada; Zone: Saskatchewan  
- Country: Canada; Zone: Yukon Territory  

Click on "BACK" to go up one level.  
Now create the Ontario Provincial Tax Zone:  
Click Insert  

- Zone Name: Ontario PST Zone  
- Description: PST (only when shipping to Ontario)  

Now click on the newly created "Ontario PST Zone" row to drill down one level to "Sub Zones"  
Click INSERT to create new sub-zone:  

- Country: Canada  
- Zone: Ontario  

Click on "BACK" to go up one level.  
Now create the HST Tax Zone:  
Click Insert  

- Zone Name: Eastern Canada - HST Zone  
- Description: NS, NB, NL  

Now click on the newly created "HST Zone" row to drill down one level to "Sub Zones"  
Click INSERT to create new sub-zone:  

- Country: Canada; Zone: Nova Scotia  
- Country: Canada; Zone: New Brunswick  
- Country: Canada; Zone: Newfoundland  

Do NOT create a separate Tax ZONE for Shipping. You will simply use the "Canada" tax zone for the GST Shipping tax CLASS (below).  

Important: this means that SHIPPING GST will only be charged to destinations within Canada, but NOT charged on exports. 
According to Canada Customs & Revenue Agency (1-800-959-5525), you do *NOT* charge GST on the shipping fee for EXPORTS.  

STEP (3): Create the "Tax Classes"  

Note: You can only assign ONE Tax CLASS to a product.  
But since we want shipping GST to show up separately, we will make a separate Tax CLASS just for it.  

Locations/Taxes > Tax Classes  

create TWO (2) tax classes:  

- Tax Class Title: GST/HST/PST Class  
- Description: All taxable goods  

- Tax Class Title: GST on Shipping  
- Description: GST on shipping within Canada  

STEP (4): TAX RATES  

Here is where it all comes together: Tax Rates.  
Tax RATES associate Tax ZONES & Tax CLASSES to determine the correct Tax Rate.  

**HINT:** The "DESCRIPTION" is what shows up on the invoice, so use it judiciously!!!!!!!!!!!!!  

Locations/Taxes > Tax Rates  

create SIX (6) Tax Rates:  

- Tax Class Title: GST/PST/HST Class  
- Zone: Canada GST Zone  
- Tax Rate (%): 6.0000  
- Description: 6.0% GST  
- Priority: 1  

**HINT:** Insert your GST# as part of DESCRIPTION and it will show up on invoice !!!  
**HINT:** Leave PRIORITY at "1" for a non-cumulative tax (i.e. Ontario)  

- Tax Class Title: GST/PST/HST Class // **HINT:** Yes, this is the same one you just used  
- Zone: Ontario PST Zone  
- Tax Rate (%): 8.0000  
- Description: 8.0% PST (Ontario)  
- Priority: 1  

**HINT:** Leave PRIORITY at "1" for a non-cumulative tax (i.e. Ontario)  
but change to "2" for cumulative tax (i.e. You are a Quebec store)  

- Tax Class Title: GST/PST/HST Class // **HINT:** Yes, this is the same one you just used  
- Zone: HST Zone  
- Tax Rate (%): 14.0000  
- Description: 14% HST  
- Priority: 1  

That takes care of taxes on products. And now, the Shipping taxes:  

- Tax Class Title: GST Shipping Class  
- Zone: Canada GST Zone  
- Tax Rate (%): 6.0000  
- Description: 6.0% GST on shipping  
- Priority: 1  

- Tax Class Title: GST Shipping Class  
- Zone: Ontario PST Zone  
- Tax Rate (%): 8.0000  
- Description: 8.0% PST (shipping)  
- Priority: 1  

- Tax Class Title: GST Shipping Class  
- Zone: HST Zone  
- Tax Rate (%): 14.0000  
- Description: 14% shipping HST  
- Priority: 1  

 **HINT:** The above will calculate PST on shipping. Although there might  
 be a tendency to think of shipping as a PST exempt service, in fact  
 the Ontario Ministry of Finance says that for calculating the PST,  
 "The total selling price includes delivery, mailing, transportation, or  
 handling charges, but does not include the GST". With the above set-up,  
 the PST for the shipping gets calculated (albeit separately).  
 If you wanted them calculated together, you could assign "GST/PST/HST Class"  
 as the Tax Class when setting up the shipping method.  
 Personally, I prefer to break it out separately.  

STEP (5): Specify the appropriate Tax Class for SHIPPING MODULES  

MODULES > SHIPPING  

Edit whichever shipping module(s) you are using.  

Tax Class: GST Shipping Class  

**SEE PREVIOUS HINT** 

STEP (6): Specify the appropriate Tax for PRODUCTS  

This may take some time....  

CATALOG > Categories/Products  

Drill down to each product. Click EDIT  

TAX CLASS: "GST/PST/HST CLASS"  

==============  
The following SQL statement could be helpful:  


`UPDATE products SET products_tax_class_id = 1 WHERE products_model NOT LIKE 'GIFT%';`


(you'd need to confirm that the desired products_tax_class_id = 1, first )  

**===============  
Example Output:  
===============**  

Shipping to Ontario:  

Sub-Total: $69.00  
Per Item (Best Way): $10.00  
8.0% PST (Ontario) + 6.0% GST: $9.66  
6.0% GST (shipping) + 8.0% PST (shipping): $ 1.40  
Total: $90.06  

Shipping into the HST zone (NB, NS, or NL):  

Sub-Total: $69.00  
Per Item (Best Way): $10.00  
14% HST: $9.66  
14% shipping HST: $ 1.40  
Total: $90.06  

Shipping to Canada, but non-HST, and non-Ontario:  
Sub-Total: $69.00  
Per Item (Best Way): $10.00  
6.0% GST: $ 4.25  
6.0% GST (shipping): $ 0.60  
Total: $83.74  

Shipping to non-Canada zone:  
Sub-Total: $69.00  
Per Item (Best Way): $10.00  
Total: $79.00  

