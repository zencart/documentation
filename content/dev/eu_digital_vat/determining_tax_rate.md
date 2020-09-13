---
title: Tax Rate
description: Setting the EU Digital VAT tax rate 
weight: 4
---

Determining Tax Rate
============

In essence, this is really just a problem of defining correct  Zone/Geo Zone definitions for EU member states, and Design75's post at https://www.zen-cart.com/showthread.php?213763-Digital-Seller-New-2015-EU-Digital-VAT-Affects-You&p=1265814#post1265814 may be useful here.

However there are some gotchas to look out for.
With standard goods in Zen Cart where the supplier is in the EU, prices are shown with tax included, and the tax rate is determined by the Store Country.
However with Digital Goods, the VAT is determined by the customers country. For a guest account/not logged in customer we don't know the customer country. This could mean that prices initially displayed will change once we actually determine the customer country, a really quick way to generate abandoned carts.

The only real way to help mitigate this, is to do some initial geoIP.
