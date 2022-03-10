---
title: Setting up a test environment 
description: Using a Local Web Server to create a Development Environment
category: Running
weight: 10
---

It's not good to deploy untested changes directly onto your live store!  Doing so can lead to outages and lost sales.

Instead, it's best to test and debug changes (including new plugins) 
on a test store.

You have two options for setting up a test environment:

1. Testing Locally: Creating a test store on your own PC
2. Testing on your Server: Creating a test store on your server

---

# Testing Locally

Using [XAMPP](https://www.apachefriends.org/) (Windows, Mac, Linux) or [MAMP](https://www.mamp.info/) (Windows, Mac), you can create a test environment on your own computer for your Zen Cart. 

For the remainder of this document, these tools will be referred to as **AMP** for convenience. 

## 1. Make a backup of your files and database 

Follow the procedure specified in [how do I backup my store?](/user/running/backup/)

## 2. Set your store on your local computer. 

- Put your files at the webroot defined in your **AMP**.
- Load your database and create a database user. 

## 3. Update your configure.php files 

You will need to go through this file and set each entry to point to your local environment. 

## 4. Try a simple update to see if things work. 
Try updating (for example), `includes/languages/YOURTEMPLATE/english.php` and, then refresh your browser page and make sure the change appears. 

---

# Testing on your Server

This is not as good as a local test environment, but better than putting untested changes on your live site and potentially breaking your store.


## 1. Create a new test store on your server

Create a NEW database in cPanel called `test_store`. Create a database user that has full permissions to access this database. 

Use the backup that you just made from your live site to fill the database with data. (See [restoring the database](/user/running/backup/#to-restore-your-database).)

Create a new folder on your server called  `test_store`.  Copy the files from your live store directory into this folder 

## 2. Prepare the configure.php files

In your `test_store` folder, update the `includes/configure.php` and `admin/includes/dist-configure.php` files:  
- Set the path names to your test store.
- Set the database name to `test_store`.
- Set `DB_SERVER_USERNAME` and `DB_SERVER_PASSWORD` to the new database user and password you created in the first step.


