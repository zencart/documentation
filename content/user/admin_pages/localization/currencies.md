---
title: Currencies 
category: admin_pages
weight: 10
---


Zen Cart comes preconfigured with several currencies, including the US dollar, the Euro, the Pound, the Canadian Dollar, and the Australian Dollar.  

You may add a new currency, or edit the existing ones.

![Currencies in Zen Cart](/images/currencies.png) 

## Adding Currencies

To add a new currency, click on the new currency button. You will then enter the information about this new currency in the input area. After you finish entering the new information, click on the Insert button to save this new currency entry.

### Title

This is the name of the new currency, like _Canadian Dollar_ or _Mexican Peso_.

### Code

This is the three-character ISO 4217 international name for the currency you just described, like _CAD_ for _Canadian Dollar_, _MXN_ for _Mexican Peso_, _USD_ for _US Dollar_, or _JPY_ for _Japanese Yen_, etc. Note that to use the automated currency conversion feature (see the explanation for the _update currencies_ button below), this code must be the correct one for that currency. If you don't know the international code for the currency you want to add, you can find it in several places:

*   In [ISO standard 4217](https://www.iso.org/iso-4217-currency-codes.html) 
*   On Wikipedia, at the entry for [ISO 4217](http://en.wikipedia.org/wiki/ISO_4217)
*   On XE.COM, which in addition to the [ISO 4217](http://www.xe.com/iso4217.htm) have the list of [symbols used for most currencies](http://www.xe.com/symbols.htm), ($ for Dollar, ₭ for Euro, £ for Pound, ¥ for Yen, etc.), as well as [currency conversion](http://www.xe.com/ucc/) between almost all world currencies (you'll need that for the **Value** field below if you want to manually process currency conversions as opposed to using the automated currency converter (see the explanation for the _update currencies_ button below), don't know what the usual currency conversion rate is between your currency and that one).

### Symbol Left

If, when this currency is displayed, some symbol usually appears before (to the left of) the amount when it is displayed, enter that here. If no symbol commonly appears before the amount (like CA$ for Canadian Dollar) leave this field blank. This is separate from, and in addition to _Symbol Right_ below.

### Symbol Right

If, when this currency is displayed, some symbol usually appears after (to the right of) the amount when it is displayed, enter that here. If no symbol commonly appears before the amount (like CAN for Canadian Dollar) leave this field blank. This is separate from, and in addition to _Symbol Left_ above.

### Decimal Point

This is where you indicate what symbol appears between whole and fractional amounts of this currency. For U.S. and Canadian dollars, this is a period; in some countries it is a comma.

### Thousands Point

This is where you indicate what symbol appears between thousands of whole amounts of this currency. For U.S. and Canadian dollars, this is a comma; in some countries it is a period.

### Decimal Places

This indicates the number of decimal places appear to the right for this currency. U.S. and Canadian dollars have two digits after the decimal point. Some currencies may have four or six.

### Value

This is the value of the other currency relative to the default currency for your store. Your default currency should have a value of exactly 1\.

If you are going to use the automatic conversion feature (see the _Update Currencies_ button below), then you can simply leave this field blank (or enter zero, both are the same) and let the website update the value.

If you do not wish to use the automatic conversion feature, here are some examples for conversions. Note that these are sample values, you will want to know what the usual conversion rate is at the current time as currency rates can fluctuate.

<table>

<tbody>

<tr>

<th>If Your default Currency is</th>

<th>And you wanted to create a new currency of</th>

<th>And the price of that currency in your default currency is</th>

<th>You would use this for the amount in the _value_ field.</th>

</tr>

<tr>

<td>US Dollar</td>

<td>Euro</td>

<td>1.27</td>

<td>0.7835</td>

</tr>

<tr>

<td>US Dollar</td>

<td>British Pound</td>

<td>1.86</td>

<td>0.5367</td>

</tr>

<tr>

<td>US Dollar</td>

<td>Canadian Dollar</td>

<td>0.8840</td>

<td>1.1312</td>

</tr>

<tr>

<td>US Dollar</td>

<td>Mexican Peso</td>

<td>0.0921</td>

<td>10.858</td>

</tr>

<tr>

<td>Euro</td>

<td>US Dollar</td>

<td>0.7836</td>

<td>1.2726</td>

</tr>

<tr>

<td>British Pound</td>

<td>Euro</td>

<td>0.6849</td>

<td>1.46</td>

</tr>

<tr>

<td>British Pound</td>

<td>Vietnam Dong</td>

<td>0.0000335444</td>

<td>29,811.25</td>

</tr>

<tr>

<td>Canadian Dollar</td>

<td>Euro</td>

<td>1.4435</td>

<td>0.6927</td>

</tr>

<tr>

<td>Canadian Dollar</td>

<td>Mexican Peso</td>

<td>0.1042</td>

<td>9.59908</td>

</tr>

<tr>

<td>Mexican Peso</td>

<td>Euro</td>

<td>13.8570</td>

<td>0.0721657</td>

</tr>

<tr>

<td>Japanese Yen</td>

<td>US Dollar</td>

<td>0.0087</td>

<td>114.655</td>

</tr>

</tbody>

</table>

### Set as Default

If this is the default currency for this store, you will want to check this box. Note it may require some manual changes, as is indicated in the box, thus you might want to set this before loading any pricing data.

After you finish, click on the _Insert_ button to save this new currency entry. If you decide you do not want this entry, click on _cancel_ and the new entry will not be added.

## Update Currencies

If you have the correct ISO 4217 code in the _code_ column, you can click on the _update currencies_ button to have the site request current exchange rate values from various conversion sites on the Internet for all currencies that have a correct ISO 4217 code, and the website will obtain current values and automatically correct the exchange rates.

Rates that are correctly converted will be listed in green at the top of the page. Rates that were not correctly converted will be listed in red. The website will probably try more than one converter if it has a failure in converting a particular currency. Pay attention to any red items in case you may have misspelled the ISO 4217 code for that currency, as it will not have been correctly updated. Any that were not correctly updated (either because of error or because the conversion site did not have the correct values for that currency) will have to be manually updated using the edit feature.

Once you have verified that clicking the Update Currencies button operates correctly and without errors, you can optionally create a [cron job](/user/first_steps/hosting/#cron) in your hosting company's control panel to run the update automatically on a scheduled basis. The command to give it is as follows. Work with your hosting company's tech support team if you need help with determining the correct path and the correct php binary to call.

```
php /full/server/path/to/admin/currency_cron.php
```

## Editing an existing currency

If you only need to correct the exchange rate, you can use the _update currency_ button to change all conversions on your website. If, however the automatic conversion does not work for one or more currencies or you need to change something else (for example, you entered Russian Rubles using code RUS instead of RUB), you would need to change that. Click on the line showing the currency you want to change. The right arrow will appear in the action column, then click on the _edit_ button.

A series of entry fields, same as provided for the _add new currency_ button will appear, only the values of those fields will be loaded with the current values. Change any fields as appropriate, then once you are finished, click on the _update_ button to save these changes. If you decide you do not want these changes, click on _cancel_ to leave the original values intact.

## Deleting an existing currency

If you no longer want a particular currency, click on the line showing the currency you want to delete. The right arrow will appear in the action column, then click on the _delete_ button. You will be asked to confirm if you want to delete that currency. Click on the _delete_ button again to do so, or click the _cancel_ button if you do not wish to delete this particular currency.

If you are deleting all currencies except your "default" currency, be sure to set that Default currency's exchange rate Value to 1.0000.

## Not displaying the Currencies box

If you only operate with one currency, Euro for example, you may wish to delete all others and set the exchange value to 1.

With just one currency in use, you will most likely want to stop the currency selection box from being displayed.

To do this:

1.  From the Tools menu, click "Layout Boxes Controller".
2.  find 'sideboxes/currencies.php' in the list. It may be near the bottom. Click it.
3.  set both "Left/Right Column Status" and "Single Column Status" to off.
4.  Click Update.

