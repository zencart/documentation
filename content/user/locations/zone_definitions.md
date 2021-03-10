---
title: Creating Zone Definitions 
description: Recipes for common Zone Definitions 
category: locations 
aliases: 
    - /user/localization/zone_definitions
weight: 10
---

If you are unclear on how zones are used in Zen Cart, please see the help pages for [Zones](/user/admin_pages/locations/zones/) and [Zone definitions](/user/admin_pages/locations/zones_definitions/). 

Zone Definitions can be created by adding each entry one at a time in the admin, or can be created quickly with some SQL commands that can be run in the Zen Cart Admin from the `Tools > Install SQL Patches` menu. 

Be careful when creating Zone Definitions such as Zone Definitions for the United States.  

```
Country: United States  
Zone: All Zones  
```

is the United States with All Zones that includes all 50 States, DC, US Islands and Territories such as Puerto Rico and the US Virgin Islands and the Armed Forces.  

If you need to distinguish your definition of the United States, then you need to specifically add the setting for the  

```
Country: United States  
Zone: (specific Zone here)  
```

### To manually create a Zone using the Zen Cart Admin 
Suppose you want to create a zone containing Alaska and Hawaii only.  
Here are the required steps: 

- Go to Admin > Locations > Zones Definitions.  Press the Insert button. 
- Enter a name (we will use "Non Continental US") and a description (Alaska and Hawaii). Press Enter
- A new row appears with the zone name "Non Continental US." In the Infobox on the right, press the Details button. 
- Press Insert, and select Country = "United States" and Zone = "Alaska".  Press Insert. 
- Press Insert, and select Country = "United States" and Zone = "Hawaii".  Press Insert. 
- You're done!  You now have a new zone you can use anywhere Zone restriction is allowed, such as a shipping module's configuration. 

### To create a Zone for the US Continental 48 States & DC

```
INSERT INTO `geo_zones` (`geo_zone_name`, `geo_zone_description`, `last_modified`, `date_added`)   
VALUES   
('48 Lower States', '48 States + DC', NULL, '2008-02-01 12:12:12');  
SET @geo_zone_id=last_insert_id();

INSERT INTO `zones_to_geo_zones` (`zone_country_id`, `zone_id`, `geo_zone_id`)   
VALUES  
(223, 1, @geo_zone_id),  
(223, 4, @geo_zone_id),  
(223, 5, @geo_zone_id),  
(223, 12, @geo_zone_id),  
(223, 13, @geo_zone_id),  
(223, 14, @geo_zone_id),  
(223, 15, @geo_zone_id),  
(223, 16, @geo_zone_id),  
(223, 18, @geo_zone_id),  
(223, 19, @geo_zone_id),  
(223, 22, @geo_zone_id),  
(223, 23, @geo_zone_id),  
(223, 24, @geo_zone_id),  
(223, 25, @geo_zone_id),  
(223, 26, @geo_zone_id),  
(223, 27, @geo_zone_id),  
(223, 28, @geo_zone_id),  
(223, 29, @geo_zone_id),  
(223, 31, @geo_zone_id),  
(223, 32, @geo_zone_id),  
(223, 33, @geo_zone_id),  
(223, 34, @geo_zone_id),  
(223, 35, @geo_zone_id),  
(223, 36, @geo_zone_id),  
(223, 37, @geo_zone_id),  
(223, 38, @geo_zone_id),  
(223, 39, @geo_zone_id),  
(223, 40, @geo_zone_id),  
(223, 41, @geo_zone_id),  
(223, 42, @geo_zone_id),  
(223, 43, @geo_zone_id),  
(223, 44, @geo_zone_id),  
(223, 45, @geo_zone_id),  
(223, 47, @geo_zone_id),  
(223, 48, @geo_zone_id),  
(223, 49, @geo_zone_id),  
(223, 51, @geo_zone_id),  
(223, 53, @geo_zone_id),  
(223, 54, @geo_zone_id),  
(223, 55, @geo_zone_id),  
(223, 56, @geo_zone_id),  
(223, 57, @geo_zone_id),  
(223, 58, @geo_zone_id),  
(223, 59, @geo_zone_id),  
(223, 61, @geo_zone_id),  
(223, 62, @geo_zone_id),  
(223, 63, @geo_zone_id),  
(223, 64, @geo_zone_id),  
(223, 65, @geo_zone_id);  
```

### To create a Zone for the US 50 States & DC

```
INSERT INTO `geo_zones` (`geo_zone_name`, `geo_zone_description`, `last_modified`, `date_added`) 
VALUES 
('50 States', '50 States + DC', NULL, '2008-02-01 12:12:12');
SET @geo_zone_id=last_insert_id();

INSERT INTO `zones_to_geo_zones` (`zone_country_id`, `zone_id`, `geo_zone_id`) 
VALUES
(223, 1, @geo_zone_id),
(223, 2, @geo_zone_id),
(223, 4, @geo_zone_id),
(223, 5, @geo_zone_id),
(223, 12, @geo_zone_id),
(223, 13, @geo_zone_id),
(223, 14, @geo_zone_id),
(223, 15, @geo_zone_id),
(223, 16, @geo_zone_id),
(223, 18, @geo_zone_id),
(223, 19, @geo_zone_id),
(223, 21, @geo_zone_id),
(223, 22, @geo_zone_id),
(223, 23, @geo_zone_id),
(223, 24, @geo_zone_id),
(223, 25, @geo_zone_id),
(223, 26, @geo_zone_id),
(223, 27, @geo_zone_id),
(223, 28, @geo_zone_id),
(223, 29, @geo_zone_id),
(223, 31, @geo_zone_id),
(223, 32, @geo_zone_id),
(223, 33, @geo_zone_id),
(223, 34, @geo_zone_id),
(223, 35, @geo_zone_id),
(223, 36, @geo_zone_id),
(223, 37, @geo_zone_id),
(223, 38, @geo_zone_id),
(223, 39, @geo_zone_id),
(223, 40, @geo_zone_id),
(223, 41, @geo_zone_id),
(223, 42, @geo_zone_id),
(223, 43, @geo_zone_id),
(223, 44, @geo_zone_id),
(223, 45, @geo_zone_id),
(223, 47, @geo_zone_id),
(223, 48, @geo_zone_id),
(223, 49, @geo_zone_id),
(223, 51, @geo_zone_id),
(223, 53, @geo_zone_id),
(223, 54, @geo_zone_id),
(223, 55, @geo_zone_id),
(223, 56, @geo_zone_id),
(223, 57, @geo_zone_id),
(223, 58, @geo_zone_id),
(223, 59, @geo_zone_id),
(223, 61, @geo_zone_id),
(223, 62, @geo_zone_id),
(223, 63, @geo_zone_id),
(223, 64, @geo_zone_id),
(223, 65, @geo_zone_id);  

```

### To create a Zone Definition for the Rest of the World, excluding the United States, you can use:

```
INSERT INTO geo_zones (geo_zone_name, geo_zone_description, last_modified, date_added)   
VALUES   
('<span class="highlight">Rest</span> of the <span class="highlight">World</span>', 'All Countries Except United States', NULL, CURDATE());  
SET @geo_zone_id=last_insert_id();

INSERT INTO zones_to_geo_zones (zone_country_id, zone_id, geo_zone_id, date_added)   
SELECT countries_id , 0, @geo_zone_id, CURDATE()   
FROM countries   
WHERE countries_iso_code_3 NOT IN ('USA');  
```

### To create a Zone Definition for the Rest of the World, excluding the United States and Canada, you can use:

```
INSERT INTO geo_zones (geo_zone_name, geo_zone_description, last_modified, date_added)   
VALUES   
('International', 'All Countries Except USA and Canada', NULL, CURDATE());  
SET @geo_zone_id=last_insert_id();

INSERT INTO zones_to_geo_zones (zone_country_id, zone_id, geo_zone_id, date_added)  
SELECT countries_id , 0, @geo_zone_id, CURDATE()  
FROM countries  
WHERE countries_iso_code_3 NOT IN ('USA','CAN');  
```

### To create a Zone Definition for the Rest of the World, excluding the United Kingdom, you can use:

```
INSERT INTO geo_zones (geo_zone_name, geo_zone_description, last_modified, date_added)   
VALUES   
('International', 'All Countries Except United Kingdom', NULL, CURDATE());  

INSERT INTO <span class="highlight">zones_to_geo_zones</span> (zone_country_id, zone_id, geo_zone_id, date_added)   
SELECT countries_id , 0, @geo_zone_id, CURDATE()   
FROM countries   
WHERE countries_iso_code_3 NOT IN ('GBR');  
```


