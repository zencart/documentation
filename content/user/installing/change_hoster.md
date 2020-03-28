---
title: Moving to another server 
description: How do I move my Zen Cart to another server? 
category: installing 
weight: 10
---

**FIRST:**  If you are moving your site, DO NOT UPGRADE AT THE SAME TIME!!!   Do your upgrade BEFORE moving, or AFTER moving, but never DURING the move. Otherwise you'll typically run into problems that can't be quickly resolved because you've got too many server issues confused into the picture. YOU HAVE BEEN WARNED!

1\. On your **NEW host**, create a new MySQL **database**. Note the username, password, database name, and host name (usually localhost).

2\. Using your [FTP tool](/user/first_steps/useful_tools/#ftp-tools), go to your **NEW host** and upload a **fresh NEW install** using the same version files that you built your other site on.... this will make sure that you get the proper settings in your [configure.php files](/user/miscellaneous/configure). 

a. Install.  When asked about the database-table-prefix during Database-Setup, use the same prefix that your old store uses. You'll find that in the `DB_PREFIX` setting of your old store's configure.php files.

b. Test it.  

c. Make **backups** of the NEW server's `/includes/configure.php` and `/admin/includes/configure.php` files by downloading them (FTP) to your PC.  

3\. On your **OLD host**, Make a **COMPLETE backup** of your DATABASE and STORE.  
a. Use either the [Backup MySQL Database](https://www.zen-cart.com/downloads.php?do=file&id=7) contribution to do the backup of your database, or use phpMyAdmin to export your entire database.  Include the "DROP" tables command, and under Data, choose "Complete Inserts" and "Extended Inserts".  
Save the SQL file to your PC for later.     Click here for 
advice on [doing a backup](/user/running/backup). 

b. Download all your old site's files via FTP (or if you have the option, zip them up on the server and download the zip)  

4\. Now **upload your OLD files over the NEW files** on the NEW server, WITH TWO EXCEPTIONS: Don't overwrite the `/includes/configure.php` and `/YOURADMIN/includes/configure.php` files on the NEW server.

5\. Go back to phpMyAdmin on your **NEW server**.  

a. Select your NEW database (that you installed the NEW Zen Cart into)  

b. DROP all the tables. (Check them all and scroll down and on "With Selected..." select DROP. Confirm Yes.)  

c. Click on Import and click Browse.  

d. Select the SQL file you made in step 3a when you exported your old database, and click Go.  

6\. If you're running ZC v1.5.1 or older, grab the 
[Fix Cache Key](https://www.zen-cart.com/downloads.php?do=file&id=8)
utility.  Upload and run this file.  **This is only required for 
Zen Cart 1.5.1 or older.**

7\. You're done. Open your store and admin areas to see it all ready to go!

8\. You should review all your email settings in Admin->Configuration->Email Options -- especially any SMTP server/account settings, and of course all your email addresses.

9\. Once your new site is up and running, you should DELETE the database and all the PHP files/folders, etc from the OLD server.  There's no point leaving that data behind for prying eyes or worse.

## A Note About NameServers And Timing

On a store that's taking live orders, you need to prevent orders from being taken in the old site once you've made your backup to move to the new site.  
So, make the following adjustments to the steps above:  

a) BEFORE taking the backup in Step 3, first login to your old site's admin, and set Admin->Configuration->Website Maintenance->Down For Maintenance = TRUE.  

b) AFTER step 5 or 6, login to your NEW store's admin, and set Down For Maintenance = FALSE.  

c) NEVER disable down-for-maintenance in the OLD site. Once you've copied the database from it, you don't want to take any more orders in the old site, else they'll be lost.  

d) Once your nameserver updates have propagated (up to 48 hours), you should be able to delete the files and database from the old server.  

**NOTE:** This means your store will appear as down-for-maintenance until the DNS/Nameserver details are propagated to the region where your customers connect online. Once the propagation is done, they will see the new site on the new server, and be able to place orders.

**ADVANCED TIP:**
If you know 3 or 4 days or maybe a week ahead of time that you're going to do this sort of move, get your old hosting company to change the TTL (Time To Live) setting on your domain DNS settings to 240 (4 hours). This will help speed the effects of propagation.  
Then, a couple days after you've completed the move, and propagation is completed, change the TTL back to normal values (whatever your new hosting company prefers to use).

**NOTE:** This FAQ handles moving a cart to a new server.
If you just want to move your cart to another folder on the 
same server, 
please see [this FAQ instead](/user/installing/move_cart/). 

