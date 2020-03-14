---
title: Detailed Upgrading Instructions
category: Upgrading
weight: 20
---

Preamble worth reading: [How-do-I-rebuild-my-site-on-the-new-version-instead-of-upgrading](https://www.zen-cart.com/entry.php?3-How-do-I-rebuild-my-site-on-the-new-version-instead-of-upgrading). 

## 3 EASY STEPS TO UPGRADE ZEN CART

NOTE: For each new release, there are important documents in the [/docs](https://www.zen-cart.com/docs/) folder of the Zen Cart ZIP file.  Please check this folder for any special notes about the version you are upgrading from/to.  

## Getting Started 

This is a basic guide to upgrading Zen Cart®. If you have not yet installed Zen Cart®, please see the [/docs/1.readme_installation.html](https://www.zen-cart.com/docs/1.readme_installation.html) file for installation instructions.  

To upgrade Zen Cart®, you'll need the same basic tools you used to install and customize it in the first place: An FTP program, a text editor friendly to HTML/PHP code, phpMyAdmin or equivalent access to your MySQL database, and your Control Panel for managing your webspace.  

Additionally, you will find a file-comparison tool.  See the list of [Useful Tools](/user/first_steps/useful_tools/) for suggestions.  Note that free tools offer 2-way comparison. The more advanced paid-for tools offer 3-way comparisons which can be very handy, but costly.

Upgrading follows 3 easy steps. We suggest you take your time going through each stage carefully and methodically. Don't rush the process. And as always, be sure you keep good backups first.  

We highly recommend you pay special attention to getting familiar with the demo data in the new version, so that you can become comfortable with the many new features contained in the new release.  

<div>

## Compatibility

First, check whether your server is compatible with the version you're trying to install: [Server Requirements for Zen Cart versions](/user/first_steps/server_requirements/). 

## 1\. Preparation

Unzip a copy of the new version of Zen Cart®, upload it to your webserver into a "<span class="filename">demo</span>" folder, and install the new version into a separate database, and include the Demo products. This is just for a place for you to play with the new version and get used to its new features. These can be deleted after conversion is complete.  

Study the new features, and the documented changes to the template structures, as well as the "changelog". Use the demo products in the demo shop as examples. See also the supporting documentation provided with the new release.  

Make a full backup of your database (dump to SQL file). Store this file on your PC for later reference.  

Make a full backup of your site files (ftp to your PC and zip it up for safe-keeping).  
Keep the backup on your PC to use in next steps. Perhaps call this folder "<span class="filename">\zen_backup</span>".  

Now let's find out the differences/customizations details between your site and the original Zen Cart® files.  (You can find older versions here: [http://sourceforge.net/projects/zencart/files/](http://sourceforge.net/projects/zencart/files/) )  

Unzip a copy of the original Zen Cart® files for the version you _originally installed_ or last upgraded from (ie: perhaps v1.3.9 or even 1.5.1). This should be placed in a separate working folder on your PC (perhaps "<span class="filename">\zen_orig</span>").  

Make a list of any add-ons you have installed, for later reference.  

Run a tool like [WinMerge](http://winmerge.sf.net/) to compare the "Original" Zen Cart® files in "<span class="filename">\zen_orig</span>" against your working backup files in "<span class="filename">\zen_backup</span>".  
Note all the files that are "different". In WinMerge, double-click on each file and note what the differences are.  
If the differences are just language defines for display text, those will be simple to carry forward.  
If the differences are actual programming/code differences, you will need to make detailed notes in order to carry over those changes to the new new new version.  
Any mods/add-ons you've installed will likely contain many programming changes, and may not be fully compatible with the newer Zen Cart® release.  

Your list of add-on's may help you narrow down the source of any differences you're finding between versions. You may have to download the add-on again to take a look at the readme or code contained in it. You may have to contact the author to ask for an updated version.  

As you make your list of changed files, etc, at this stage, you may want to move things into the Zen Cart® template-override structure, if you haven't already done so. See the [Template System Documentation](/wiki/index.php/Customisation_-_Templates#Introduction) for help on the template system.  

</div>

<div>

## 2\. Execution

Download and unzip the latest Zen Cart® version to your PC. This will be in a 3rd directory (perhaps "<span class="filename">\zen_new</span>"), separate from the other two folders compared above.  

Using the list of files you made earlier, go through each "changed" file, and make your changes from the old version into the new version.  
Simple language edits will be just a matter of copy-and-paste.  
Programming changes to core components will be more difficult and require significant testing.  
You may find WinMerge handy at this stage to apply edits as well. However, you will see many extra differences that may not be related to your own customizations, or that may conflict. Be careful making changes to program code.  

Note that there will be several changes you will have to make to files that you have overridden using the template overrides system. Thus, you'll want to compare files from 
`/includes/templates/MYTEMPLATE/*` to `/includes/template/template_default/*`, and the same with language file overrides, sideboxes, etc.  

</div>

<div>

## 3\. Testing

Make a NEW database to install the new version of Zen Cart® into.  

If the last backup you made of your data is older than the last order that might have been processed or customer registration, make a fresh database backup.  
Restore your database from the backup in step #1 earlier into your NEW database just created.  

If your <span class="filename">/zen_new</span> folder doesn't have "<span class="filename">/includes/configure.php</span>" and "<span class="filename">/admin/includes/configure.php</span>" files, copy them from your old store folder.  

EDIT your "<span class="filename">/zen_new/includes/configure.php</span>" file and ensure that the DIR_FS_CATALOG and DIR_WS_CATALOG and DIR_FS_SQL_CACHE (and other path settings too) correctly match your NEW directory structure on the server.  

EDIT your "<span class="filename">/zen_new/includes/configure.php</span>" file and ensure that your DATABASE_NAME matches your NEW database. Also verify database username and password in case that information has changed. Save this file, and be sure to upload it as part of the next step:  

Upload the files from your modified "new version" (created in step 2) to your server, into an alternate folder, perhaps called "<span class="filename">/store_new</span>".  

Run <span class="filename">/zc_install/index.php</span> and choose "_Upgrade_" when prompted. (Don't select "Install", or you will overwrite your database.) (If "Upgrade" is not offered, then the installer was unable to connect to your database to confirm what version its structure is at. Check your configure.php settings.)  

Test your customizations. Edit as needed. Compare with the test/demo install performed earlier, as needed.  

When satisfied that all is OK, go live.  
If significant time has passed since you did your last backup, you may want to repeat the steps in this "Testing" section again, using a fresh backup from your live shop. You don't need to re-upload files again ... simply do the database restore, and run the installer to do the database upgrade again.  

To go live, put your shop into "Down for Maintenance" mode in the admin area. Be sure to add your IP address to the list of allowed addresses to get into the site for previewing.  
This can be done easiest by renaming "<span class="filename">store_new</span>" to "<span class="filename">store</span>". (You'll have to rename "store" to something else first.)  
Test it to be sure that things are operating as desired. If you have small problems to repair, turn "Down for maintenance" on and off again as necessary.  

## NOTES

Remember that your "configure.php" files on your server are typically set to read-only, and thus in order to upload them will require that you mark those files read-write before uploading.  Be sure to put them back to read-only after uploading.</div>
