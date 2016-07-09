# Database Schema

There are 4 tables associated with definitions. The purpose of the tables is to allow for the defining of groups of definitions , that can then be assigned to location.

This allows for easier instantiation, as opposed to instantiating each definition separately.

##listingbox_locations

fields :-

1. location_key varchar(40) : should be in uppercase with underscores separating words
2. location_name varchar(255) : A string containing a friendly name for the location.

Used to define a location. e.g. If you want to display a group of definitions beneath the shopping cart, you would create a entry here

```
INSERT INTO `zencart`.`listingbox_locations` (`location_key`, `location_name`) VALUES ('SHOPPING_CART', 'Shopping Cart');
```

## listingboxgroups

fields :-

1. group_id int(11) autoincrement : table key. Not user alterable
2. group_name varchar(255) : A string containing a display friendly name for the group

Used to define a group. You may want to define a group that contains say featured, new, special definitions. You would first create an entry here.

```
INSERT INTO `zencart`.`listingboxgroups` (`group_id` ,`group_name`) VALUES (NULL , 'Featured - Specials - New');
```
## listingboxes_to_listingboxgroups
fields:-

1. listingbox varchar(80) : the name of a definition class
2. group_id int(11) : the group_id from listingboxgroups table that you want this listingbox assigned to.
3. sort_order int(11) : if you have multiple listingboxes assigned to a group you can determine the sort order with this field.

##listingboxgroups_to_locations

fields:-

1. group_id int(11) : the group_id from listingboxgroups table that you want to assign to the location.
2. location_key varchar(40) : the location_key from the listingbox_locations table that you are assigning the group to
3. sort_order int(11) : as its possible to assign multiple groups to a location, you can determine the sort order with this field.

Used to assign listingboxgroups to a location. Note you can assign multiple groups to the location.
