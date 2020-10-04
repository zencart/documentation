---
title: VAT setup instructions
description: Calculating taxes in a VAT jurisdiction
category: taxes
aliases: 
    - /user/localization/vat 
    - /user/locations/vat 
weight: 10
---

Here's how to do it, and I am assuming here that you want to have VAT added for goods shipping to any EEC country.

Admin > Locations/Taxes > Zone Definitions

Click on insert.

```
Name of Zone: EEC VAT Zone
Description: EEC Countries Zone for VAT
```

Now click on the details button, or the folder Icon next to EEC VAT Zone

```
Click on Insert - Select United kingdom for the country - Click on insert
Click on Insert - Select Germany for the country - Click on insert
Click on Insert - Select France for the country - Click on insert
```
repeat this for all countries in the EEC

Now goto to Admin > Locations/Taxes > Tax Classes make sure that there is an entry called Taxable Goods. If not, create one.

Now goto to Admin > Locations/Taxes > Tax Rates

Click on new tax rate

```
Tax Class Title should be - Taxable Goods
Zone should be - EEC VAT Zone
Tax Rate - 17.5
Description - VAT 17.5% or similar
priority can be left blank - Click on insert
```

Note the above assumes you have no zone definitions/tax rates already set up. If you do just delete them.

Now any goods that you wish to charge VAT on must have their _Tax Class_ set to _Taxable Goods_. You can do this on the [product edit screen](/user/products/product_edit/).

Finally, in Admin > Configuration > My Store make sure that _Basis of Product Tax_ is set to *Shipping*.

