---
title: Zones 
description: Zen Cart Zones Admin Page 
category: admin_pages
weight: 20
---

FIXME - page needs work

Defines subdivisions of countries such as states/provinces or counties for tax or shipping purposes.

There are two kinds of zones in Zen Cart: zones and zones definitions (sometimes referred to as geo_zones). Zones are local; that is, counties or provinces within a larger entity such as a state or country. Zones definitions are generally on the state or country level.


For example, you may have a zones definition European Union which contains all the countries in the European Union. Then you might define zones for each of those countries, containing the provinces for that country.


You always have to define at least one zones definition, and every location (country or state) you plan to sell to should be included in one of your zones definitions. But unless you need to distinguish among provinces or counties (for tax or shipping, for example), you really don't need to define zones.


If you are in one of the very few and fortunate states which have no sales tax (such as Delaware) then you could simply have a single zone for all of the United States. If you ship to customers who have a sales tax exmption on file or are exempt (such as diplomatic personnel), then you could have a zone called exempt and indicate sales tax there at zero.


The zones and zones definitions are used to couple 
[Tax Rates](/user/admin_pages/locations/tax_rates) and 
[Tax Classes](/user/admin_pages/locations/tax_classes) to geographic locations. 
For example, you may ship to all states in the USA, but since your store is located in Florida, you only need to charge sales tax to customers in Florida. You can define two zones definitions: one containing all the states except Florida, and one containing just Florida. Then you can specify the Tax Rate that the zone Florida should use.


Now, if your state has separate tax rates for different cities or counties (like California), then you will need to establish one for each city or county in order to be able to account for all sales made and apportion them for each city or county according to your sales tax return.


Some Shipping Modules (such as the zones shipping module) also work with geographic zones. These zones are specified in the module itself, and are independent of the zones definitions you make. This means you can specify different shipping rates, for example, for countries in the same zone definition.


