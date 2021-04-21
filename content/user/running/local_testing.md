---
title: Setting up a local test environment 
description: Using a Local Web Server to create a Development Environment
category: Running
weight: 10
---

Using [XAMPP](https://www.apachefriends.org/) (Windows, Mac, Linux) or [MAMP](https://www.mamp.info/) (Windows, Mac), you can create a test environment on your own computer for your Zen Cart. 

For the remainder of this document, these tools will be referred to as **AMP** for convenience. 

**Note:** If you don't feel comfortable doing this, the second best option for creating a test cart is creating a new folder on your live server.  This option is discussed [here](/user/running/local_testing/#testing-on-your-server/). 

---

# Testing Locally

## 1. Make a backup of your files and database 

Follow the procedure specified in [how do I backup my store?](/user/running/backup/)

## 2. Set your store on your local computer. 

- Put your files at the webroot defined in your **AMP**.
- Load your database and create a database user. 

## 3. Update your configure.php files 

You will need to go through this file and set each entry to point to your local environnment. 

## 4. Try a simple update to see if things work. 
Try updating (for example), `includes/languages/YOURTEMPLATE/english.php` and, then refresh your browser page and make sure the change appears. 

---

# Testing on Your Server

For large complicated changes such as upgrades, it may make sense to do a 
final test on your production server.  This way, configuration changes 
between your local and live environments can be discovered and dealt with, 
and your store will work as expected when you go live.  

The instructions below assume you are using cPanel. 

## 1. Creating a Test Site using cPanel

For purposes of this exercise, we will use a cPanel account `high64` with `home/high64/public_html` as the location of your existing site, and `your_site.com` as your current Zen Cart website. 

Using the terminology from [the glossary](/user/first_steps/glossary/), we have: 
* Webroot: `home/high64/public_html`
* YOURSITE: `your_site.com`
* YOURACCOUNT: `high64`
* YOURACCOUNTFOLDER: `home/high64/`

**Note:** In your actual installation, the store may be located in a subfolder (e.g. `home/your_account/public_html/store`), but for this exercise, we will assume it is not.  See [/user/first_steps/deployment_configurations/] for more examples of how stores can be set up; this is deployment model 1.

### A. Create a NEW database in cPanel that uses your standard name and add `157c`. 

The Create New Database will present you with the prefix of ***high64*** and a block to fill in the final part of the new database name.  To keep track of things, the new database for testing 1.5.7c could be set to ***high64_157c*** making it easy to tell it from other databases.  ***high64_test*** or anything that identifies the database to you is fine.

Unless you feel it is necessary to give this new database a separate user and password, you can scroll down in the Database Section to **Add User to Database**.  Sekect a current user in the **User block** and make sure the new database name is showing in the **Database** block.  Click on Add and a new screen will appear.

Select the **ALL PRIVILEGES** option and click on **Make Changes**.  Your new database is ready and waiting for data.  You will need that username and password in **Step E**, below

### B. Download Zen Cart and Upload the Zip to Your cPanel

Whether upgrading, testing, or creating your first Zen Cart installation, always obtain the files from [the official Zen Cart download location](/user/first_steps/get_zen_cart/).  In this case, download the latest version to your hard drive.  You will want to create a folder for it and the mods you will be adding/testing with the test site.

With cPanel's File Manager, navigate to ***/home/your_account/***.  This is known as "*above webroot*."  If your cPanel File Manager loads with /public_html, just clock on Up One Level to be "above the root."  You should see a Home symbol followed by (/home/your_account).  From the menu bar, click on Upload and drag the Zen Cart zip file into the upload block.  If you do not see an upload block, use the Select File button to browse your computer for the zip installation file.

Once the file is uploaded, click on the Go Back button to return to the File Manager.  You should still be above the root and the zip file should be listed in the right-hand column under name.  If not, click on the Reload option to have the file appear.

Again, make sure this is a **Zen Cart distributed zip file**.  All distribution zip files from Zen Cart will extract to a folder.  If it is NOT a Zen Cart distributed zip file, you may be dropping files everywhere.  ***Backup here just in case.***

Select the installation zip file and click on the Extract option on the menu bar.  In the case of 1.5.7c, the zen-cart-v1.5.7c-########.zip will extract to a folder named zen-cart-v1.5.7c-######## that matches the file you uploaded.

### C. Creating the Test Folder.

Select the folder created by unzipping the Zen Cart file and rename it something like ***_test***, ***_upgrade***, ***_OPC_tryout***, etc.  Something that is easy for you to remember.  Prefixing with the underscore (*_*) makes the folder less likely to be mistaken for an in-use site.

### D. Creating a Sub_Domain.

In cPanel, navigate to the Domains Section and click on the Subdomains option.  Since we are using ***_test*** as our folder for this exercise, we will call the Subdomain ***test***.

In the Subdomain, enter ***test***.

Make sure the domain is showing the ***your_site.com*** that matches the site you are going to test/upgrade.

Leave the Document Root selection empty and click on Create.

You now have a Subdomain of ***test.your_site.com*** ready to be setup.

### E. Setting the PHP for the Test Site.

If your cPanel does NOT have a **Software** Section with a selection of **MultiPhP Manager**, you may need your host's help on this step.

If you don't have MultiPhP Manager, ask your host to set the PHP for the **\_test** folder that you created.  

If you do have MultiPHP Manager, go to the **Software** Section in the cPanel and open **MultiPHP Manager**.  Set the PHP version appropriately. 

If **test.your_site.com** is not already listed with the needed version of PHP, select the box in front of **test.your_site.com** and select a version of PHP in the drop-down titled **PHP Version** above the listing area.  

The PHP version you select should be the latest supported version that works with your version of Zen Cart.  The [PHP Version Matrix](/user/first_steps/server_requirements/#php-version) will show you the versions of PHP that work well with the version of Zen Cart you are testing. 

For instance, with Zen Cart 1.5.7c, you could use any version of PHP from 5.6 to 8.0.
**However**, at the time of writing, PHP 5.6 is past end of life, and PHP 8.0 is a brand new release, so PHP 7.4 might be the best choice. 

### F.  Run zc_install.

In your browser, navigate to **test.your_site.com/zc_install**.  If everything is correct so far, you should get the **Installation Screen**.  Follow the directions to load Zen Cart on your test site.

The test site should offer you the option of https:// if you have an SSL installed on your server.  This is one of the advantages of testing on your remote server.

Whether to add example products is up to you and your purpose for creating the test site.  If you can quickly and easily create your own products in the Zen Cart backend, don't add example products. 

Let the installation process create the *two* configure.php files for you.  All you have to provide is the database username and password. 

### G.  Finalize Installation.

Copy down all the pertinent usernames, passwords, and the new admin folder name.  Then, delete the zc_install folder in the cPanel File Manager.  You may need to re-install that folder later if you want to upgrade a previous version's database but, you have that folder you created on your computer with all the files you need so, re-loading the zc_install folder is simple with the cPanel File Manager.  **Renaming the zc_install folder is not recommended.**  If someone stumbles across the renamed folder, they can use it to wreak havoc with your test site.

### H.  Test/Upgrade

You now have a fully functioning, intial installation of the version you uploaded to the server.

## 2.  Creating a Test Site on a non-cPanel server.

Some servers do not use cPanel due to the cost involved for the host.  Still, most hosts have some form of "Control Panel" that acts pretty much the same as cpanel.  Each section may be named slightly different but, you should be able to figure out the steps that result in the test folder creation, database creation, subdomain assignment, PHP selection, etc.

DirectAdmin and Plesk are two of the most common cPanel alternatives.  If you find yourself with one of cPanel's alternatives and are stuck on a step, just open a thread on the forum and someone will be glad to point you in the right direction.  Be sure to mention the cPanel alternative you are using.

