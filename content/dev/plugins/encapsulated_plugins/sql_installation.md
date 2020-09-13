---
title: Plugin SQL Installation
description: 
weight: 40
layout: docs
---

Plugins may need to create/alter database tables and/or insert/amend data in database tables.

The plugin installer allows two methods for doing this. Using `.sql` files containing just sql statements or
using a class based migration system.

## Plain SQL Files

Create a plain .sql file called `install.sql` with the SQL statements you need for installation. Be sure to make your installation robust in the face of prior partial or failed installs (e.g. use `IF NOT EXISTS`, `INSERT IGNORE` and so forth). 

    CREATE TABLE IF NOT EXISTS reward_master (
                               rewards_products_id INT( 11 ) NOT NULL AUTO_INCREMENT PRIMARY KEY,
                               scope INT( 1 ) NOT NULL DEFAULT '0',
                               scope_id INT( 11 ) NOT NULL DEFAULT '0',
                               point_ratio DOUBLE( 15, 4 ) NOT NULL DEFAULT '1',
                               bonus_points DOUBLE( 15, 4 ) NULL,
                               redeem_ratio DOUBLE( 15, 4 ) NULL,
                               redeem_points DOUBLE( 15, 4 ) NULL,
                               UNIQUE unique_id ( scope , scope_id ));

    INSERT IGNORE INTO reward_master
    (rewards_products_id ,scope ,scope_id ,point_ratio ,bonus_points, redeem_ratio, redeem_points)
    VALUES (NULL , '0', '0', '1.0000', NULL, 0.01, NULL);


The sql file should reside in

- zc_plugins

    - rewardPoints

        - v1.0.0

            - Installer

                - install.sql


**Warning** As Zen Cart currently uses mainly `MyISAM` tables, there is no way to safely roll back any
  installer sql if an error occurs. Some support for rollback may be added later (using generated migrations).

Note that an uninstall script (called `uninstall.sql`) may be placed in the same folder. 


## SQL Installer Classes

If you have more complex needs when creating schemas or seeding the database, instead of 
using a plain SQL install file as above, you can use a class based method.

An example of this is provided in the `DisplayLogs` plugin, in `zc_plugins/DisplayLogs`.  The class `ScriptedInstallBase` may be extended to permit the execution of complex logic during the install and uninstall process. 

The two key methods that must be implemented in a class which extends `ScriptedInstallBase` are `executeInstall` and `executeUninstall`, which run the installation and de-installation logic.  


