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

### Currently Supported SQL Commands

- DROP TABLE IF EXISTS \<table name>;
- DROP TABLE \<table name>;
- CREATE TABLE IF NOT EXISTS \<table name> \<additional sql>;
- CREATE TABLE \<table name> \<additional sql>;
- TRUNCATE TABLE \<table name>;
- REPLACE INTO \<table name> \<additional sql>;
- INSERT INTO  \<table name> \<additional sql>;
- INSERT IGNORE INTO \<table name> <additional sql>;
- ALTER TABLE \<table name> \<additional sql>;
- RENAME TABLE \<table name> TO \<table name>;
- UPDATE \<table name> \<additional sql>;
- DELETE FROM \<table name> \<additional sql>;
- DROP INDEX \<index name> ON \<table name>;
- CREATE INDEX \<index name> ON \<table name> \<additional sql>;
- SELECT \<fields> FROM \<table name> \<additional sql>;
- SELECT \<fields> FROM \<table name> \<join type> JOIN \<table name> \<additional sql>
    
Where: 
- \<table name> is the name of the table(s) which may require a suffix adding
- \<additional sql> is additional valid sql for the statement. **It must not contain any table names that may require prefixing**
- \<index name> is the name of the index to be created/dropped
- \<join type> is the type  INNER, OUTER, etc.
    
Note:
- There must be exactly one space before \<table name>.
- The statement before the first \< must be single spaced.
- There can be multiple JOIN statements in a select.
- Every statement must end with ";".
- Sub selects are not available.    


## SQL Installer Classes

If you have more complex needs when creating schemas or seeding the database, instead of 
using a plain SQL install file as above, you can use a class based method.

An example of this is provided in the `DisplayLogs` plugin, in `zc_plugins/DisplayLogs`.  The class `ScriptedInstallBase` may be extended to permit the execution of complex logic during the install and uninstall process. 

The two key methods that must be implemented in a class which extends `ScriptedInstallBase` are `executeInstall` and `executeUninstall`, which run the installation and de-installation logic.  


