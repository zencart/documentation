---
title: Plugin SQL Installation
description: 
weight: 40
layout: docs
---

Plugins might need to create/alter database tables and/or insert/amend data in database tables. 

The plugin installer allows two methods for doing this: 

1. A class-based approach where each database alteration is done with PHP code. This approach also allows for upgrading between versions when you release updates.
2. Using `.sql` files containing just SQL statements. This should only be used in VERY simple scenarios, where upgrades will never be needed.


## SQL Installer Classes

If you have more complex needs when creating schemas or seeding the database, instead of using a plain SQL install file as above, you can use a class based method, by extending ScriptedInstallBase as `/Installer/ScriptedInstaller.php` in your plugin. See [Installer Classes](/dev/plugins/encapsulated_plugins/installer_classes/) for details.

IF YOUR PLUGIN PROVIDES UPGRADES WHICH NEED DATABASE CHANGES, then you MUST use the [Installer Classes](/dev/plugins/encapsulated_plugins/installer_classes/), since there is no way to offer plain `.sql` file upgrades.

An example is provided in the `DisplayLogs` plugin, in `zc_plugins/DisplayLogs/[version]/Installer/ScriptedInstaller.php`.

Briefly, three key methods that must be implemented in a class which extends `ScriptedInstallBase` are `executeInstall` and `executeUninstall` and `executeUpgrade`, which run the installation, de-installation and upgrade logic, respectively. They should return `true` on success, and `false` on failure. They can set `$this->errorContainer->addError($severity=0, $logMessage, $booleanShowLogToUser, $userMessage)` if any errors need to be logged and/or shown to the user.



## Plain SQL Files

If your needs are VERY simple, and upgrades will never be necessary, you could use just a plain .sql file:

Create a plain SQL file called `install.sql` with the SQL statements you need for installation. Be sure to make your installation robust in the face of prior partial or failed installs (e.g. use `IF NOT EXISTS`, `INSERT IGNORE` and so forth). 

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

    - PluginName

        - v1.0.0

            - Installer

                - install.sql
                - uninstall.sql


**Warning** With this `install.sql` approach, there is no way to safely roll back any installer SQL if an error occurs.

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
  

***Notes***:

- There must be exactly one space before \<table name>.
- The statement before the first \< must be single spaced.
- There can be multiple JOIN statements in a select.
- Every statement must end with a semi-colon (`;`).
- Sub selects are not available.    


