---
title: Zones Module Setup 
description: How to price shipping by destination zone 
category: shipping 
weight: 10
---


By default, the Zones shipping module comes with support for 3 zones. This can be easily altered with a coding change by editing the Zones Shipping Module file (If you make this change and your Zones module is already installed/active, you'll need to record your settings, click Remove, click Install, and re-enter all your settings. Otherwise your change will have peculiar visual side-effects).  

`includes/modules/shipping/zones.php`

```
  // CUSTOMIZE THIS SETTING FOR THE NUMBER OF ZONES NEEDED  
  $this->num_zones = 3;  
```

Next, you will want to activate the module by going to 
[Admin > Modules > Shipping](/user/admin_pages/modules/shipping/).  
A list of all shipping modules should appear. Click on Zone Shipping. Click on the install button.

**<font color="#800000">YOU WILL LOSE YOUR CURRENT SHIPPING RATES AND OTHER SETTINGS (in this module) IF YOU "REMOVE" THIS SHIPPING METHOD.</font>** 

**Make sure you keep a backup of your shipping settings somewhere at all times.**

If you want an additional handling charge applied to orders that use this method, set the Handling Fee field.

Next, you will need to define which countries are in each zone. Determining this might take some time and effort. You should group a set of countries that has similar shipping charges for the same weight. For instance, when shipping from the US, the countries of Japan, Australia, New Zealand, and Singapore have similar shipping rates. As an example, one of my customers is using this set of zones:  

1: USA  
2: Canada  
3: Austria, Belgium, Great Britain, France, Germany, Greenland, Iceland, Ireland, Italy, Norway, Holland/Netherlands, Denmark, Poland, Spain, Sweden, Switzerland, Finland, Portugal, Israel, Greece  
4: Japan, Australia, New Zealand, Singapore  
5: Taiwan, China, Hong Kong  

When you enter these country lists, enter them into the Zone X Countries fields, where "X" is the number of the zone. They should be entered as two character ISO country codes in all capital letters. They should be separated by commas with no spaces or other punctuation. For example:  

1: US  
2: CA  
3: AT,BE,GB,FR,DE,GL,IS,IE,IT,NO,NL,DK,PL,ES,SE,CH,FI,PT,IL,GR
4: JP,AU,NZ,SG  
5: TW,CN,HK  

Now you need to set up the shipping rate tables for each zone. Again, some time and effort will go into setting the appropriate rates. You will define a set of weight ranges and the shipping price for each range. 

These values are entered as [colon-separated pairs](/user/running/colon-separated-pairs/). 

For instance, you might want an order than weighs more than 0 and less than or equal to 3 to cost 5.50 to ship to a certain zone.

You would then use the following setting in the Shipping Table: 

```
3:5.5
```

You should combine a bunch of these rates together in a comma delimited list and enter them into the "Zone X Shipping Table" fields where "X" is the zone number. For example, this might be used for Zone 1:

1:3.5,2:3.95,3:5.2,4:6.45,5:7.7,6:10.4,7:11.85, 8:13.3,9:14.75,10:16.2,11:17.65,12:19.1,13:20.55,14:22,15:23.45

The above example includes weights over 0 and up to 15\. Note that units are not specified in this explanation since they should be specific to your locale.

## CAVEATS

At this time, it does not deal with weights that are above the highest amount defined. For now, you could have one last very high range with a very high shipping rate to discourage orders of that magnitude.

For instance: 999:1000

If you want to be able to ship to any country in the world, you will need to enter every country code into the Country fields. For most shops, you will not want to enter every country. This is often because of too much fraud from certain places. If a country is not listed, then the module will add a $0.00 shipping charge and will indicate that shipping is not available to that destination.

<font color="#800000">THE ORDER CAN STILL BE COMPLETED AND PROCESSED!</font>

Lastly, there is a limit of 255 characters on each of the Zone Shipping Tables and Zone Countries. This can be changed in the database to suit your needs.

