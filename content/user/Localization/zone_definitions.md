---
title: Zone Definitions 
category: localization 
weight: 10
---

Zone Definitions can be created by adding 1 by 1 each Zone or can be created quickly with some SQL commands that can be run in the Zen Cart Admin from the Tools ... Install SQL Patches ...  

Be careful when creating Zone Definitions such as Zone Definitions for the United States.  
Country: United States  
Zone: All Zones  

is the United States with All Zones that includes all 50 States, DC, US Islands and Territories such as Puerto Rico and the US Virgin Islands and the Armed Forces.  

If you need to distinguish your definition of the United States, then you need to specifically add the setting for the  
Country: United States  
Zone: (specific Zone here)  

Be careful to note the `geo_zone_id` in each of the INSERTs below. They are unique from one another so that they do not conflict with each other. You also need to ensure that they are unique on your site, meaning, that you have not already used the `geo_zone_id` for another Zone Definition. You can check this by going to your Zen Cart Admin and checking the Localization-&gt;Zone Definitions.  If you click on the Zone Definition, you will see in the URL the `zID=XX` which will indicate the `geo_zone_id` that is being used.  

### To create a Zone for the US Continental 48 States & DC

```
INSERT INTO `geo_zones` (`geo_zone_id`, `geo_zone_name`, `geo_zone_description`, `last_modified`, `date_added`)   
VALUES   
(21, '48 Lower States', '48 States + DC', NULL, '2008-02-01 12:12:12');  

INSERT INTO `zones_to_geo_zones` (`zone_country_id`, `zone_id`, `geo_zone_id`)   
VALUES  
(223, 1, 21),  
(223, 4, 21),  
(223, 5, 21),  
(223, 12, 21),  
(223, 13, 21),  
(223, 14, 21),  
(223, 15, 21),  
(223, 16, 21),  
(223, 18, 21),  
(223, 19, 21),  
(223, 22, 21),  
(223, 23, 21),  
(223, 24, 21),  
(223, 25, 21),  
(223, 26, 21),  
(223, 27, 21),  
(223, 28, 21),  
(223, 29, 21),  
(223, 31, 21),  
(223, 32, 21),  
(223, 33, 21),  
(223, 34, 21),  
(223, 35, 21),  
(223, 36, 21),  
(223, 37, 21),  
(223, 38, 21),  
(223, 39, 21),  
(223, 40, 21),  
(223, 41, 21),  
(223, 42, 21),  
(223, 43, 21),  
(223, 44, 21),  
(223, 45, 21),  
(223, 47, 21),  
(223, 48, 21),  
(223, 49, 21),  
(223, 51, 21),  
(223, 53, 21),  
(223, 54, 21),  
(223, 55, 21),  
(223, 56, 21),  
(223, 57, 21),  
(223, 58, 21),  
(223, 59, 21),  
(223, 61, 21),  
(223, 62, 21),  
(223, 63, 21),  
(223, 64, 21),  
(223, 65, 21);  
```

### To create a Zone for the US 50 States & DC

```
INSERT INTO `geo_zones` (`geo_zone_id`, `geo_zone_name`, `geo_zone_description`, `last_modified`, `date_added`) 
VALUES 
(37, '50 States', '50 States + DC', NULL, '2008-02-01 12:12:12');

INSERT INTO `zones_to_geo_zones` (`zone_country_id`, `zone_id`, `geo_zone_id`) 
VALUES
(223, 1, 37),
(223, 2, 37),
(223, 4, 37),
(223, 5, 37),
(223, 12, 37),
(223, 13, 37),
(223, 14, 37),
(223, 15, 37),
(223, 16, 37),
(223, 18, 37),
(223, 19, 37),
(223, 21, 37),
(223, 22, 37),
(223, 23, 37),
(223, 24, 37),
(223, 25, 37),
(223, 26, 37),
(223, 27, 37),
(223, 28, 37),
(223, 29, 37),
(223, 31, 37),
(223, 32, 37),
(223, 33, 37),
(223, 34, 37),
(223, 35, 37),
(223, 36, 37),
(223, 37, 37),
(223, 38, 37),
(223, 39, 37),
(223, 40, 37),
(223, 41, 37),
(223, 42, 37),
(223, 43, 37),
(223, 44, 37),
(223, 45, 37),
(223, 47, 37),
(223, 48, 37),
(223, 49, 37),
(223, 51, 37),
(223, 53, 37),
(223, 54, 37),
(223, 55, 37),
(223, 56, 37),
(223, 57, 37),
(223, 58, 37),
(223, 59, 37),
(223, 61, 37),
(223, 62, 37),
(223, 63, 37),
(223, 64, 37),
(223, 65, 37);  

```

### To create a Zone Definition for the Rest of the World, excluding the United States, you can use:

```
INSERT INTO geo_zones (geo_zone_id, geo_zone_name, geo_zone_description, last_modified, date_added)   
VALUES   
(40, '<span class="highlight">Rest</span> of the <span class="highlight">World</span>', 'All Countries Except United States', NULL, CURDATE());  

INSERT INTO zones_to_geo_zones (zone_country_id, zone_id, geo_zone_id, date_added)   
SELECT countries_id , 0, 40, CURDATE()   
FROM countries   
WHERE countries_iso_code_3 NOT IN ('USA');  
```

### To create a Zone Definition for the Rest of the World, excluding the United States and Canada, you can use:

```
INSERT INTO geo_zones (geo_zone_id, geo_zone_name, geo_zone_description, last_modified, date_added)   
VALUES   
(22, 'International', 'All Countries Except USA and Canada', NULL, CURDATE());  

INSERT INTO zones_to_geo_zones (zone_country_id, zone_id, geo_zone_id, date_added)  
SELECT countries_id , 0, 22, CURDATE()  
FROM countries  
WHERE countries_iso_code_3 NOT IN ('USA','CAN');  
```

### To create a Zone Definition for the Rest of the World, excluding the United Kingdom, you can use:

```
INSERT INTO geo_zones (geo_zone_id, geo_zone_name, geo_zone_description, last_modified, date_added)   
VALUES   
(35, 'International', 'All Countries Except United Kingdom', NULL, CURDATE());  

INSERT INTO <span class="highlight">zones_to_geo_zones</span> (zone_country_id, zone_id, geo_zone_id, date_added)   
SELECT countries_id , 0, 35, CURDATE()   
FROM countries   
WHERE countries_iso_code_3 NOT IN ('GBR');  
```


