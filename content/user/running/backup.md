---
title: Backups - how do I do a site backup? 
description: how do I do a site backup in Zen Cart? 
category: running
weight: 10
---

**NOTE:** A full backup of your Zen Cart site has **TWO** parts: 

- A copy of all your Zen Cart files, and  
- A copy of your database

## A\. Backup your files 

Use your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to make a copy of all the files on your website, by copying them from your webserver to a folder on your business computer. Preferably the directory/folder on your computer should be named by today's date so that you can distinguish between backups.  

Having this gives you not only an up-to-date set of files on your server, but also a reference point for either making changes or for making comparisons in case something gets compromised or damaged on your webserver. You can either use this set of files to restore the program back to your website, or to diagnose a problem if one occurs.  

**NOTE:** Keeping multiple separate versions on your computer is prudent, in case something is changed unexpectedly or accidentally. So, archiving these downloaded files is wise, to a USB key or cloud based backup. 

## B. Backup your Database  

### Using phpMyAdmin to make a Database Backup
1\. Open phpMyAdmin  

2\. Select your database from the dropdown (usually on the left side), so that its tables are displayed (they usually display on the right side).  

3\. Click on the Export tab. (**NOTE:** Be sure you've already selected your database from the pulldown BEFORE clicking on the Export tab)  

4\. Now make the appropriate setting selections based on your version of phpMyAdmin:  

The ideal settings to do a backup via phpMyAdmin are shown below. Settings not mentioned can be left to their defaults.  

You will be presented with a choice of "Quick Backup" or "Custom." Choose "Custom", and then make the following selections:  

- Output: Leave all the other settings under Output as defaults, except maybe **Compression**, which you may wish to change to "zipped" (for Windows) or "gzipped" (for Mac/Linux)  
- Object creation options: **check the box next to DROP TABLE**  

5\. Click **Go** to do the export. It will give you the option to save the file to your PC. BE SURE TO SAVE IT to an appropriate spot on your PC. 
To have a redundant backup, save a copy to a thumb drive or upload it to a cloud account such as 
Google Drive.

6\. If you have an older version of MySQL installed or wish to see what defaults may be best to support export, then see: [How Can I do a Site Backup or Use phpMyAdmin for Database Backup](https://www.zen-cart.com/content.php?144-how-can-i-do-a-site-backup-or-use-phpmyadmin-for-database-backup)

### Using the Backup MySQL Plugin to make a Database Backup

On hosts that permit the use of `exec()`, you can use the 
[Backup MySQL Plugin](https://www.zen-cart.com/downloads.php?do=file&id=7)
to create your database backup, and then download the resultant file
from `YOURADMIN/backups` to your local computer.  Again, you will 
want to save a copy to a thumb drive or upload your backup to a cloud account so that you have 
redundancy. 
<br /><br />

--- 

## TO RESTORE YOUR DATABASE:

- Open phpMyAdmin  
- From the dropdown menu, select the database you wish to restore INTO  
- Click on the "Import" tab (in older phpMyAdmin versions, you might have to click the "SQL" tab instead)  
- Click on the Browse button, and select the file you downloaded when making the backup  
- You probably want to UNCHECK the "Allow interrupt of import" in the Partial Import section.  
- Click Go  

**NOTE:** If you are going to be RESTORING to a server running different version of MySQL than what your backup came from, you should be careful about which additional switches you check. Ask your hosting company or server administrator for guidance if you are uncertain.
