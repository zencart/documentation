---
title: Databases 
category: first_steps
weight: 1
---
The database is a collection of tables. Tables are like spreadsheets, storing data in rows and columns, related to whatever the structure of that table is for. For customers, it means email addresses, passwords, etc. For address books, it means all the address info for each customer. For orders, all the order details. For products, the details of each aspect of each product. And so on. You could look at a database as a multi-sheet spreadsheet, but way more optimized and efficient in how it automatically handles indexing and storage/retrieval.  

## Where do I find the database files?

A database is not stored in any files that are directly accessible to you as a storeowner. Instead, you access it via phpMyAdmin or similar tools, and query (request) data from the database according to what you wish to read from it.  
In the case of taking a [backup](http://tutorials.zen-cart.com/index.php?article=103), you're exporting the entire database content into one great big file that can be used for offline storage, or restoring if needed. That's the only way *you* will ever see the database as "a file".  
(Aside: Technically speaking, it *does* store everything in "files", but they're machine-code files, and meaningless to you unless you're a SQL and Server guru with super-advanced abilities to understand 0s and 1s with your eyes closed.)  

## How are databases connected to Zen Cart?

When installing Zen Cart, you tell Zen Cart which database to store its data in. Those details are stored in the configure.php files (usually by zc_install when you're installing the site for the first time).  

## How many databases does Zen Cart use?

Generally speaking, a Zen Cart store only uses **one** database at a time.**  
SO ... THAT MEANS YOU SHOULD NEVER RESTORE or IMPORT a different database into your live store's database unless you're absolutely certain that you wish to WIPE OUT the existing data!!!**  

**Exceptions:** 
Some (ie: most "good") hosting accounts allow multiple databases without additional fees. Some do not. In the case of servers where only *one* database is allowed but multiple Zen Cart stores are setup in the same hosting account for different domains/sites, Zen Cart supports the use of "table prefixes" to differentiate between stores sharing that database. It identifies the tables which it uses *within* that database by the `DB_PREFIX` setting in your configure.php file.  

So, you could have `store1_` as a prefix to all the table-names for that store, and `zen_` as a prefix to the tables for another store, and so on. That's why the table-prefixes exist.  

Some hosting companies have auto-installers that quickly dump a ZC site onto someone's account. Instead of setting up multiple databases, those usually engage the `DB_PREFIX` as `zen_` by default so they can keep the tables for the store separate from the tables they auto-install for a blog or a forum or a gallery or whatever.  While this makes managing the database more difficult for the storeowner, it makes the hosting company's auto-installer easier for them because it means they get to cheap-out on the resources you use.
