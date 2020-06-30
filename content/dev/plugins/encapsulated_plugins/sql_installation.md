---
title: Plugin SQL Installation
description:  
weight: 40
layout: docs
---

Plugins may need to create/alter dtabase tables and/or insert/amend data in database tables.

The plugin installer allows two methods for doing this. Using .sql files containing just sql statements or
using a class based migration system.

## Plain SQL Files


    CREATE TABLE IF NOT EXISTS reward_master (
                               rewards_products_id INT( 11 ) NOT NULL AUTO_INCREMENT PRIMARY KEY,
                               scope INT( 1 ) NOT NULL DEFAULT '0',
                               scope_id INT( 11 ) NOT NULL DEFAULT '0',
                               point_ratio DOUBLE( 15, 4 ) NOT NULL DEFAULT '1',
                               bonus_points DOUBLE( 15, 4 ) NULL,
                               redeem_ratio DOUBLE( 15, 4 ) NULL,
                               redeem_points DOUBLE( 15, 4 ) NULL,
                               UNIQUE unique_id ( scope , scope_id ));

    INSERT INTO reward_master
    (rewards_products_id ,scope ,scope_id ,point_ratio ,bonus_points, redeem_ratio, redeem_points)
    VALUES (NULL , '0', '0', '1.0000', NULL, 0.01, NULL);


The sql file should reside in

- zc_plugins

  - rewardPoints

    - v1.0.0

      - Installer

        - sqlInstall

          - install.sql


**Warning** As Zen Cart currently uses mainly MyIsam tables, there is no way to safely roll back
  installer sql if an error occurs. Some support for rollback may be added later (using generated migrations).


## SQL Installer Classes

If you have more complex needs when creating schemas or seeding the database, instead of 
using a plain SQL intall file as above, you can use a class based method.




