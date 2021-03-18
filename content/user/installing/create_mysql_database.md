---
title: How do I create a MySQL database? 
description: Using cPanel to create a MySQL database 
category: installing 
weight: 10
---

To use Zen Cart, you need a database.  

## To prepare a MySQL database for Zen Cart to use:

1.  Open your hosting account's control panel.
2.  Find the "Databases" section
3.  Choose the MySQL option
4.  Click on the option to Create a database.  Enter a name for it and submit. (Record the name so you can use it later in Zen Cart).
    If you are given an option for choosing a Character Set, choose `utf8mb4`; if offered a Collation option, choose `utf8mb4_0900_ai_ci` or `utf8mb4_unicode_520_ci`.
6.  Now create a user and password. (Record these for use in Zen Cart)
7.  Now you need to "grant" or "assign" the user to the database, granting appropriate permissions.  See the section about Permissions, below.  

That's it !!  

Now in the Zen Cart Installer, on the Database Setup section, supply all of the database information you just set up: name, user, password, and host. Usually the "host" is "localhost" unless your hosting company uses a specific different configuration.  

## What Database Permissions/Privileges Do I Give to my Database User?

For the purposes of Zen Cart sites, the following permissions ("privileges") are required for the database user:  

*   SELECT
*   INSERT
*   UPDATE
*   DELETE
*   FILE  (not used by core code, but easiest to leave it checked)  

*   CREATE
*   ALTER
*   INDEX
*   DROP
*   CREATE TEMPORARY TABLES (not required by the core code, but may be required by some addons)  

*   LOCK TABLES  (not used by core code; required only for database backups)  

If you're using a cPanel hosting account, you would usually check the box for "ALL PRIVILEGES" instead of checking off individual options.  

Using any of the optional items noted above does not create any significant security risk.  Recommended approach for most storeowners is "All Privileges".
