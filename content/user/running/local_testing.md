---
title: Setting up a local test environment 
description: Using a Local Web Server to create a Development Environment
category: Running
weight: 10
---

Using [XAMPP](https://www.apachefriends.org/) (Windows, Mac, Linux) or [MAMP](https://www.mamp.info/) (Windows, Mac), you can create a test environment on your own computer for your Zen Cart. 

For the remainder of this document, these tools will be referred to as **AMP** for convenience. 

## 1. Make a backup of your files and database 

Follow the procedure specified in [how do I backup my store?](/user/running/backup/)

## 2. Set your store on your local computer. 

- Put your files at the webroot defined in your **AMP**.
- Load your database and create a database user. 

## 3. Update your configure.php files 

You will need to go through this file and set each entry to point to your local environnment. 

## 4. Try a simple update to see if things work. 
Try updating (for example), `includes/languages/YOURTEMPLATE/english.php` and, then refresh your browser page and make sure the change appears. 

