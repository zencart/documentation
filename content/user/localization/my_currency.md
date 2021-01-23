---
title: How do I use another currency instead of US Dollars? 
description: Alternate currencies in Zen Cart 
category: localization
weight: 10
---

There are two parts to configuring your currency settings: 

- Configuring whether you want to accept more than one currency
- Adding the new currency
- Optional: Enabling a currency-selection sidebox in the store
- Recommended: Update exchange rates regularly.

Go to [Admin > Configuration > My Store](/user/admin_pages/configuration/configuration_mystore/).
If you are running your shop in a language that is not English and are going to use your native currency, click on the line that says "Switch To Default Language Currency" and change the value to true. If you are going to run the cart in English, but not use US Dollars, make sure that the "Switch To Default Language Currency" is set to false.

Then go to [Admin > Localization > Currencies](/user/admin_pages/localization/currencies/).  

If your currency is in the list which is shown, click your currency, click Edit and check the box labelled *Set as default*.  Then click Save.  

If your currency is *not*  in the list which is shown, click the *New Currency* button. Fill in the information appropriate for your currency and check the box if it is to be the default for your shop. Click the *Insert* button, then after the page refreshes, click the *Update Currencies* button.

Be sure to click the *Update Currencies* button on at least a weekly basis to update all exchange rates.

If you wish to allow a dropdown menu for shoppers to change the store's displayed prices in that currency, you can enable the [Currencies Sidebox](/user/sideboxes/sidebox_list/#currencies) to appear in either the left or right sidebars.
