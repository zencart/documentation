---
title: No data in my store after moving hosts 
description: Where is my data? 
category: troubleshooting 
weight: 10
---

### Moving To Another  Server
To move your site to a new host, you should follow the instructions listed in the FAQ entitled [I want to move my Zen Cart installation to another host or a different server](/user/installing/change_hoster/).


### No Data or "1146 Table 'configuration' doesn't exist" messages

After moving, or after installation, if you're getting `1146 Table 'configuration' doesn't exist` (or a similar *doesn't exist* message), or if you're not seeing the data you imported from your old server, then you probably missed an important step in the instructions in the FAQ article mentioned above.

If it's saying that the `configuration` table doesn't exist, then it's connecting to a database somewhere, but not the one that contains Zen Cart tables.  Make sure that you've properly set the database server/host name, database name, username/password properly for the new server in your [configure.php files](/user/miscellaneous/configure/).

### DB_PREFIX
If you're importing data from another server, you **must** use the **same** setting for `DB_PREFIX` on the new server as you had on the old server. Otherwise you're telling the software to point to a set of tables in your database that 
are either incorrect or non-existent. 

`DB_PREFIX` is defined in your configure.php files.

If `DB_PREFIX` is defined as blank, then Zen Cart assumes there is no prefix added to table names.

If it is not blank, then Zen Cart adds that prefix to the start of all table names when it generates a query to extract data from the database.

So, in the case of the "configuration" table, if the prefix is left blank, then Zen Cart looks for a table named `configuration` If the prefix is defined as `zen_`, then Zen Cart looks for a table named `zen_configuration`. 


