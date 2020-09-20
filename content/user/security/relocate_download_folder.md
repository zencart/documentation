---
title: Download folder - Relocating 
description: Storing downloads outside of webroot 
category: security
weight: 10
---

With Zen Cart it is possible to relocate the "download" folder outside your 
[webroot](/user/first_steps/how_do_i_install#what-is-my-webroot) 
folder so that thieves cannot directly link to real files on your server and download without paying or being authenticated.  

To do this, you must:  

1.  Choose a download method of either "**Download by Streaming**" or "**Download by Redirect**" from **Admin > Configuration > Attribute Settings**.  
    If you're using a Linux server, either option is suitable.  
    If you're using a Windows server running IIS, you may not be able use redirects (depending on PHP version and whether or not your server allows PHP symlinks). Instead, you will need to use _**Download by Streaming**_ in order to handle secured downloads.  

2.  Use your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to move your "download" folder outside your webroot. Perhaps drag-and-drop it to a level "above" your `public_html` folder.  The method you choose for moving or creating this folder will depend on your hosting account and the tools available to you for moving folders.  

    Usually the "download" folder is located inside your store area, for example:  
    - `/home/my_user_name/public_html/mystore/download`

    You want to move it "above" your `public_html` folder, something like this:  
    - `/home/my_user_name/download`

3.  Edit your two configure.php files to show the new path to your download folder:  
    - `/includes/configure.php`
    - `/YOURADMIN/includes/configure.php`

In Zen Cart 1.5.5 and higher: 

<div class="indent">

There is no line setting `DIR_FS_DOWNLOAD` in these versions of Zen Cart.  You must *add* a line to the bottom of your configure.php files that says something like 

`define('DIR_FS_DOWNLOAD', '/home/my_user_name/download/');`
</div>

In Zen Cart 1.5.4 and lower: 

<div class="indent">

You'll need to edit the line that says this:  
  
`define('DIR_FS_DOWNLOAD', DIR_FS_CATALOG . 'download/');`
  
to look something like this:  
  
`define('DIR_FS_DOWNLOAD', '/home/my_user_name/download/');`
</div>
  
Specifically, you need to indicate the exact complete path for the webserver's filesystem that points to your download folder.  You could use your `DIR_FS_CATALOG` entry in your configure.php file as a reference, and make appropriate adjustments.  Your FTP program and/or your webserver's hosting control panel should be able to help you understand the complete path.

As an example, if your `DIR_FS_CATALOG` value is set as follows: 

`define('DIR_FS_CATALOG', '/home/jimmy/public_html/store/');`

then you would want 

`define('DIR_FS_DOWNLOAD', '/home/jimmy/download/');`
