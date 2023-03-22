---
title: Moving your Zen Cart folder 
description: Switching between subfolder and root deployment, or changing subfolder name 
category: installing 
weight: 10
---

You can install Zen Cart in the root folder of your hosting account or in a subdirectory.  See [deployment configurations](/user/first_steps/deployment_configurations/) for examples. 

If you change your mind, you can move your cart (from a [subfolder](/user/installing/subfolder/) to root or vice versa); you just have to update some settings when you do so. 

***Scenario:*** 

I have been building my cart behind the scenes at: 
`http://www.mysite.com/shop/`
I am nearly ready to go live with it at: `http://www.mysite.com/`

What steps do I need to follow to move my site to another folder 
on the same server? 

**Answer:**

- Determine the new foldername where your Zen Cart files will be running from
- In the case above, move your files from `/shop/` to the root level.  

If you are moving from `/shop/` to `/store/`, rename the folder. 

- Modify your `/includes/configure.php` and `/admin/includes/configure.php` files to point to the right folders.  Update 

```
DIR_FS_CATALOG
DIR_WS_CATALOG
DIR_WS_HTTPS_CATALOG
DIR_FS_LOGS (if present or uncommented)
DIR_FS_SQL_CACHE (if present or uncommented)
```

Note that the configure.php files are normally "read-only". You'll need to change their permissions to "writable" before you can upload your changes. Be sure to note level the permissions were at before changing, so that you can put them back to the read-only permissions again after updating.

### Older Versions (Zen Cart 1.3.9 and below)

In older versions (ie: v1.3.9h and older) you'll need to also adjust these in your `/admin/includes/configure.php` file. 

```
DIR_WS_ADMIN
DIR_WS_HTTPS_ADMIN (in admin)
DIR_FS_ADMIN (in admin)
```

- If you could not set the Session Write Directory in step 1 above, you can use a utility to do it for you. The goal is to make sure that the new path information (specifically the `DIR_FS_SQL_CACHE` setting in your new configure.php file) matches the Session Write Directory setting. If it doesn't, you may end up with difficulties logging in to the Admin area or maintaining login sessions in the store. The [Fix Cache Key Utility](https://www.zen-cart.com/downloads.php?do=file&id=8) will help you to do this if you need assistance. There is no harm running it to have it check that things are set properly. Be sure to delete the file from your server when done.

**NOTE:** This FAQ handles moving a cart to a new folder on the 
same server.  If you need to move your cart to a new server, 
please see the [FAQ on changing hosters](/user/installing/change_hoster/). 
