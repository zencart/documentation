---
title: Upgrading - Detailed Instructions
description: Zen Cart Upgrading - Detailed Instructions
category: Upgrading
weight: 10
---

Preamble worth reading: [How-do-I-rebuild-my-site-on-the-new-version-instead-of-upgrading](https://www.zen-cart.com/entry.php?3-How-do-I-rebuild-my-site-on-the-new-version-instead-of-upgrading). 

Before you begin, remember to make a [complete backup of your files and database](/user/running/backup/). 

## 3 EASY STEPS TO UPGRADE ZEN CART

**NOTE:** For each new release, there are important documents in the [/docs](https://www.zen-cart.com/docs/) folder of the Zen Cart zip file.  Please check this folder for any special notes about the version you are upgrading from/to.

This guide assumes for simplicity that you have Zen Cart installed in a folder called `store`.  This configuration allows you to run your old store and your new store side by side for testing before going live.  If you didn't install your current store in a subfolder, you can still install your new store in a subfolder for testing, and then remove the subfolder and install at the top level when it's time to go live. 


## Getting Started 

This is a basic guide to upgrading Zen Cart. If you have not yet installed Zen Cart, please see the [/docs/1.readme_installation.html](https://www.zen-cart.com/docs/1.readme_installation.html) file for installation instructions.  

Upgraders, be sure to familiarize yourself with the content of the release (and any prior releases you are upgrading through to get to the new release).  

You should review:

- Relevant **What's New** files in the [release directory docs](https://www.zen-cart.com/docs/). 
- The [Release Specific Considerations](/user/upgrading/release_specific_upgrade_considerations/) document. 

To upgrade Zen Cart, you'll need the same basic tools you used to install and customize it in the first place: An [FTP tool](/user/first_steps/useful_tools/#ftp-tools), a [text editor](/user/first_steps/useful_tools/#php-html-and-text-editors) for HTML/PHP code, phpMyAdmin or equivalent access to your MySQL database, and your Control Panel for managing your webspace.  

Additionally, you will find a file-comparison tool to be highly beneficial.  See the list of [Useful Tools](/user/first_steps/useful_tools/) for suggestions.  While the free tools offer 2-way comparison, the more advanced paid-for tools offer 3-way comparisons which can be much handier.

Upgrading follows 3 core steps. We suggest you take your time going through each stage carefully and methodically. Don't rush the process. And as always, be sure you keep good backups first.

You should also spend some time getting familiar with additions to the demo data in the new version, so that you can become comfortable with the many new features contained in the new release.  

## Compatibility

First, [check whether your server is compatible](/user/first_steps/server_requirements/) with the version you're trying to upgrade to.

## 0\. New version familiarization (optional) 

This step is helpful if you have never done this before, to give you more confidence in creating databases and uploading files.

It's also helpful just to take a tour of the new version to see how any new features work.

Install it, just like a fresh store: Unzip a copy of the new version of Zen Cart, upload it to your webserver into a `demo` folder.  Create a new demo database in cPanel, when you install the new version of Zen Cart, set it to use the new demo database.  Be sure to include the Demo products when you install. This is just for a place for you to play with the new version and get used to its new features. These can be deleted after conversion is complete.  

Study the new features, and the documented changes to the template structures, as well as the "changelog". Use the demo products in the demo shop as examples. See also the supporting documentation provided with the new release.  

When you're done with your testing, remove `demo` and the database you created for it.

## 1\. Preparation

### Make backups
Make a [full backup of your live database (dump to SQL file)](https://docs.zen-cart.com/user/running/backup/#b-backup-your-database). Store this file on your PC for later reference.

Make a [full backup of your live site files (ftp to your PC and zip it up for safe-keeping)](https://docs.zen-cart.com/user/running/backup/#a-backup-your-files). 

Keep an unzipped copy of your backup on your PC to use in the next steps. Perhaps call this folder `store`. 

### Identify (make a list of) all your existing customizations
NOTE: This is a time-consuming step.

Now let's find out the differences/customizations between your site and the original Zen Cart files.  (You can find older versions here: [http://sourceforge.net/projects/zencart/files/](http://sourceforge.net/projects/zencart/files/))

> Advanced Tip: You will probably discover that combining the following "discovery of customizations" with the "execution" step will save you time. This document is written with the assumption that you're using only a 2-way-capable comparison tool. If you have a 3-way compare tool things will go much faster: column 1 is `zc_orig`, column 2 is `store` and column 3 is `zc_new` ... and you merge (copy) any changes between columns 2-3 into column 2 where they don't clash with column 1. Anything changed between columns 1-2 is a customization you made or a plugin has made, so you want to keep that or at least merge it with whatever is new in column 3 if anything. This sounds complicated when just reading it in words, but in practice it becomes visually quite intuitive.

You may already have a list, but during this step make a list of any add-ons/plugins you have installed, for later reference. You will use this list to get updates for those plugins later. You may find that you remember additional plugins to add to this list as you do the review in the next paragraphs.

Unzip a copy of the original Zen Cart files for the version you _originally installed_ or last upgraded from (ie: perhaps v1.3.9 or even 1.5.1). This should be placed in a separate working folder on your PC (perhaps 
`zen_orig`).

Run a tool like [WinMerge](http://winmerge.sf.net/) to compare the "Original" Zen Cart files in `zen_orig` against your current live store files in `store`. 

Here we are taking a list of how your actual site is customized vs the original files.
Make note of all the files that are "different", and how.
In WinMerge you can double-click on each file and note what the differences are.

#### Types of Differences
There will be many differences:
- language defines for display text - those will be simple to carry forward.
- actual programming/code differences -- for these you will need to make detailed notes in order to carry over those changes to the new version.
- add-ons/plugins you've installed -- these often contain numerous programming changes, and may not be fully compatible with the newer Zen Cart release.

Your list of add-ons/plugins may help you narrow down the source of any differences you're finding between versions. You may have to download the add-on again to take a look at the readme or code contained in it. An updated version may already be posted, or you may have to contact the author to ask for an updated version.

#### Consider moving customizations into a standard override structure
As you make your list of changed files, this may be a good time to move your store-specific changes into the Zen Cart template-override structure, if you haven't already done so. See the [Template System Documentation](/user/template/) for help on the template system.

The benefit of moving these customizations into specific override files is that these overrides are simpler to compare/upgrade in the future, and may mean less work when it comes to the "actual" upgrade in following steps.


## 2\. Execution

Download and unzip the latest Zen Cart version to your PC. This will be in a 3rd directory (perhaps `store_new`), separate from the other two folders compared above (eg `store` and `zen_orig`).

Using the list of files you made earlier, go through each "changed" file, and re-make your changes from the old version onto the new version.  

- Simple language edits will be just a matter of copy-and-paste.

- Programming changes to core components will be more difficult and require significant testing.  

  You may sometimes find WinMerge handy at this stage to apply edits as well. However, you will see many extra differences that may not be related to your own customizations, or that may conflict. Be careful making changes to program code.  

- Note that there will be several changes you will have to make to files that you have overridden using the template overrides system. Thus, you'll want to compare files from 
`/includes/templates/MYTEMPLATE/*` to `/includes/template/template_default/*`, and the same with language file overrides, sideboxes, etc.

  While sometimes it may seem that the overrides files mean double work, it's still very useful to know that most of your non-override files won't require special attention, and you can focus your work on mainly the override files. (Again, this assumes you've diligently used overrides.)

- Install updated versions of plugins. This includes installing the files, and doing any installation/upgrade steps their documentation mentions. If database updates are required, do them. Also make detailed notes of these steps you take so you can re-do them on your live store when it comes time to do the real upgrade with real data.

- For any plugins/addons you are no longer using, do any uninstall instructions associated with them, including removing their files and removing any database components. If some of this can be done to your "live" site before actually going "live" then sometimes this makes the go-live step simpler.


## 3\. Testing

### Take a fresh backup
First, take a fresh database backup from your live store.

In your live store, go to `Admin > Configuration > Website Maintenance`.  Put the store in maintenance mode, and add your IP to the list in the `Down For Maintenance (exclude this IP-Address)` field.

Make a fresh backup of your live database. 

Create a NEW database in cPanel.  Load this database from the backup 
of your live site that you just made.

In your `store_new` folder, copy 

- `includes/dist-configure.php` to `includes/configure.php`
- `admin/includes/dist-configure.php` to `admin/includes/configure.php`

Edit these to files and set all the parameters.  Use your existing
live store as a guide.  Remember to specify your NEW database when 
filling in `DB_DATABASE`. 

Upload the files from your modified `store_new` (created in step 2) to your server, into an alternate folder, perhaps called `store_new`. 

Run `store_new/zc_install/index.php` and choose "_Upgrade_" when prompted. (Don't select "Install", or you will overwrite your database.) (If "Upgrade" is not offered, then the installer was unable to connect to your database to confirm what version its structure is at. Check your configure.php settings and be sure the `DB_*` fields correspond to your new database.)  

Test your customizations. Edit as needed. Compare with the test/demo install performed earlier, as needed.  

When satisfied that all is OK, go live.  

If significant time has passed since you created your new database, you may want to rebuild it to get any new customers or orders that have been added to the live site.

- Export your live database
- Create a new database in cPanel, and load it with the backup from your live database
- Run the `zc_install` procedure again

You don't need to re-upload files again; simply update the database. 

To go live, do the following: 

- rename your live store folder to `store_old`.
- rename `store_new` to `store`.  Edit the `includes/configure.php` and `admin/includes/configure.php` files to change the folder references from `store_new` to `store`.

Test it to be sure that things are operating as desired. If you have small problems to repair, turn "Down for maintenance" on and off again as necessary.  

Remember that your "configure.php" files on your server are typically set to read-only, and thus in order to upload them will require that you mark those files read-write before uploading.  Be sure to put them back to read-only after uploading.


## Example: 

Suppose you are currently running Zen Cart 1.5.1 and you want to upgrade to 
Zen Cart 1.5.6c.  These are the steps to use (we will skip over the New code familiarization step).


- Download your live store files, and put them in a folder called `store`.
- Download a fresh copy of Zen Cart 1.5.1, and put it in a folder called `zen_orig`.
- Compare the files in `store` to the files in `zen_orig`, noting your changes. 
- Download a fresh copy of Zen Cart 1.5.6c, and put it in a folder called `store_new`.  Apply the changes you found in the prior step to `store_new`. 
- In `store_new`, create the new configure files as follows: 
    - copy `includes/dist-configure.php` to `includes/configure.php`
    - copy `admin/includes/dist-configure.php` to `admin/includes/configure.php`
    - modify these two files, setting the values in them from your original configure files in `store`.  
    - In each file, you want two changes: `DIR_FS_CATALOG` setting should refer to `store_new` and not `_store`, and `DB_DATABASE` should refer to a new database name, not the original one. 
- Upload `store_new` to your server.  
- Make a fresh backup of your live database. 
- Create a NEW database in cPanel, using the name you used in the last step of updating your configuration files above.  Load this database from the backup of your live site that you just made. 
- point your browser to `store_new/zc_install`, which will take you through the database update process. 
- test `store_new`, going through the shopping, buying and order fulfillment process.
- When you're ready to go live, do the following: 
  - take a final backup of your live store database for safekeeping
  - In your live store, go to `Admin > Configuration > Website Maintenance`.  Put the store in maintenance mode, and add your IP to the list in the `Down For Maintenance (exclude this IP-Address)` field.
  - rename your live store folder to `store_old`.
  - rename `store_new` to `store`.  Edit the `includes/configure.php` and `admin/includes/configure.php` files to change the `DIR_FS_CATALOG` references from `store_new` to `store`, and change the `DB_DATABASE` references back to the original database name.
  - run the `store/zc_install` process to upgrade your live database.
  - test your upgrade 
  - take your store out of maintenance mode.  

## Plugins and Templates 

In the description above, I am assuming that change changes you have made are things like language file changes or maybe small code tweaks you did.  If the changes are plugins, there may be a better way than just porting the old changes forward to the new version: you can check the [plugins area](https://www.zen-cart.com/downloads.php) for an updated version of the mod.  If you don't see one, you can ask on the mod's support thread.

When it comes to templates, if you have gotten your template from the plugins area, the advice above applies.  If your template came from a commercial vendor, you should approach that vendor and ask about an upgrade. 

If you are upgrading from 1.5.4 or below, you have another decision to make: Zen Cart 1.5.5 and above are designed to be used on mobile devices as well as desktop devices.  Your older template is likely not mobile friendly, so you may wish to get one that is.  The built in [responsive classic](/user/template/other_templates/#responsive-classic-template-product-page) template in 1.5.5+ is a good start. 

