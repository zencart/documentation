---
title: Countries
category: admin_pages
weight: 10
---

Defines every country with the following information: 

- Country Name
- ISO-3166 2-letter and 3-letter country code 
- [Address format](/user/localization/address_formats/)
- Whether you ship to that country

![Countries](/images/countries.png)

Enabled countries show at the top of the list.

The address format and shipping status can be seen in the right sidebar, which is opened when a country is selected. 

![Countries - USA](/images/countries_usa.png)


## Disabling/Enabling Countries

In your Admin->Locations/Taxes->Countries screen, you can click on the green "status" icon to toggle the country's status off. The screen updates immediately with the change. If you don't see the country alphabetically in the list, it may have been previously disabled, which moves a country to the end of the list. Clicking the red icon will turn the country back on.

You may update the `status` field in the countries table in phpMyAdmin if you wish to disable many or most countries.  For example, to block sales outside the USA, you would do 

```
UPDATE countries SET status = 0 WHERE countries_iso_code_2 != 'US'; 
```

As with all database changes, make a backup before doing this.

