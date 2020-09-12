---
title: Zones 
category: admin_pages
weight: 20
---

![Zones](/images/zones.png)

There are two kinds of zones in Zen Cart: **zones** and [zone definitions](/user/admin_pages/locations/zones_definitions/) (sometimes referred to as _geo\_zones_). 

- Zones are the regions within a country defined by that country's national government.  For example, Canada is broken into Provinces. 
- Zone Definitions are groupings of zones that storeowners create to for shipping, payment and tax purposes.  

For example, you may have a zone definition **European Union** which contains all the countries in the European Union. Then you might define zones for each of those countries, containing the provinces for that country.


The zones and zone definitions are used to couple 
[Tax Rates](/user/admin_pages/locations/tax_rates/) and 
[Tax Classes](/user/admin_pages/locations/tax_classes/) to geographic locations. 
For example, you may ship to all states in the USA, but since your store is located in Florida, you only need to charge sales tax to customers in Florida. You can define two zone definitions: one containing all the states except Florida, and one containing just Florida. Then you can specify the Tax Rate that the zone Florida should use.

If your state has separate tax rates for different cities or counties (like California), then you will need to establish one zone definition for each city or county in order to be able to account for all sales made and apportion them for each city or county according to your sales tax return.

Some Shipping Modules (such as the [Zones Shipping Module](/user/shipping/zones/)) also allow you to define zones within the module itself, independent of the zone definitions you make. This means you can specify different shipping rates, for example, for countries in the same zone definition.

