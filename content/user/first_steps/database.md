---
title: Databases 
description: Where is the data stored in Zen Cart?
category: first_steps
weight: 10
---

If you are completely new to databases, please review the [basics of Zen Cart](/user/first_steps/components/). 

## Where do I find the database files?

A database is not stored in any files that are directly accessible to you as a storeowner. Instead, you access it via phpMyAdmin or similar tools, and query (request) data from the database according to what you wish to read from it.  In the case of taking a 
[backup](/user/running/backup/). 
you're exporting the entire database content into one great big file that can be used for offline storage, or restoring if needed. That's the only way *you* will ever see the database as "a file".  

## How are databases connected to Zen Cart?

When installing Zen Cart, you tell Zen Cart which database to store its data in. Those details are stored in the configure.php files (usually by zc_install when you're installing the site for the first time).  

## How many databases does Zen Cart use?

Generally speaking, a Zen Cart store only uses **one** database at a time.  

**THIS MEANS YOU SHOULD NEVER RESTORE or IMPORT a different database into your live store's database unless you're absolutely certain that you wish to WIPE OUT the existing data!!!**  

## What permissions does a database need?

See the [Installation docs](/user/first_steps/how_do_i_install/#5-have-you-created-a-database) for database creation and permissions details.

## What are prefixes? 

Zen Cart supports the use of "table prefixes" to differentiate between its own tables and the tables used by other web applications sharing the database. It identifies the tables which it uses *within* that database by the `DB_PREFIX` setting in your configure.php file.  Prefixes often have the value `zen_` or `zc_`.

Using prefixes is no longer a recommended practice; simply create one database for your Zen Cart store, and only use that database for that store. 

Prefixes are sometimes used by Zen Cart auto-installers, which are also **not recommended**.  See [how do I install](/user/first_steps/how_do_i_install/) for details. 

## How many tables are in the Zen Cart database? 

As of version 1.5.8, there are 94 tables in the Zen Cart database. 
You can see a list of them by looking at the file `includes/database_tables.php`. 

## What is the schema for Zen Cart? 

Recent releases have a schema file stored in the documentation.  Go to the [Zen Cart Schema page](/dev/schema/) to find the version which corresponds to your Zen Cart version.   If you're not sure what version you are running, take a look at the FAQ [how to find your Zen Cart version](/user/first_steps/version/). 


