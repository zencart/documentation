---
title: Fixing broken tables 
description: Common MySQL table issues 
category: Upgrading
weight: 10
---

Common problems in this class include: 

- broken auto-increments 
- corrupt indexes 

Methods of fixing them are as follows: 

- running a repair on the table from phpMyAdmin’s Operations tab or executing `REPAIR TABLE tablename;` phpMyAdmin's SQL tab
- Doing a repair from your hosting control panel’s databases page (if they don't offer phpMyAdmin)
- Manually running `REPAIR TABLE tablename;` from within `mysql` from the command line on your server, if you have `ssh` access. 

