---
title: How to Rename Your Admin Folder
category: Running
weight: 20
---

While access to your admin area is protected by the requirement of your admin password, it is recommended for additional security that you rename your _admin_ directory after installation. This way, it will be significantly harder for hackers to find your admin area or attempt any attack on breaking into it.

Before making the following changes, make sure to have a current backup of your files and your database. 

You're going to do three steps: 

A) edit the configure.php settings and upload them, 

B) rename the admin folder, 

C) test login to the new folder.   

Details are below:

## Zen Cart v1.5.x:

### A - configure.php 
If you are using v1.5.x, go to step B to rename the folder. If you are using v1.3.x, see the section below about v1.3.x which explains how to edit this file properly in that case.  

There is no need to alter the admin configure.php in v1.5.x when renaming your admin folder. Simply proceed to step B.

### B - Rename the Admin folder

Using your FTP software or your webhost's _File Manager_, find your Zen Cart _/admin/_ directory_._ Rename the directory to match the settings you just made in step A.

NOTE: DO NOT advertise this new foldername, else you defeat the entire purpose of renaming it.  And DO NOT EVER put it in your robots.txt file!

### C - Login to your admin using the new URL

To login to your admin system you will now have to visit a new URL that matches the new name used in steps A and B above.  

For example instead of visiting 

**www.example.com/<u>admin/</u>** 

visit 

**www.example.com/<u>NeW-NamE4u</u>/**  

* * *

## Zen Cart v1.3.x:

### A - (<font color="#FF0000">This step for Zen Cart v1.3.x ONLY:</font> ) 
Edit /admin/includes/configure.php

**<font color="#800080">IMPORTANT NOTE: <font size="4">If you're using Zen Cart v1.5.0 or newer, you can skip this step</font>, and proceed to step B to rename the folder using your FTP program.  With v1.5.0 there's no need to edit your configure.php file when renaming your admin folder.</font>**

Using your FTP program, download a copy of your **/admin/includes/configure.php** file to your computer.  
Using a simple text editor like notepad (or better yet, use [Notepad++](http://notepad-plus.sf.net) or [TextWrangler](http://www.barebones.com/products/TextWrangler/)), change all instances of **_admin_** to your chosen **new admin folder-name**.  

For maximum security, you may want to consider that new folder name should include numbers and a combination of upper and lower case letters. The longer you make this folder's name the more secure it will be.  


**When editing, make sure you leave all the `/` (slashes) alone.**  

<font size="5" color="#ff0000">**DO NOT USE SEARCH-AND-REPLACE TO DO THESE EDITS!!!!!!!!!!!**</font>

<font size="5" color="#FF0000">Change ONLY THE WORD <font color="#0000FF">**admin**</font>, in 3 places, AS SHOWN HERE:</font>

Change this section:

<pre> define('DIR_WS_ADMIN', '/**<font color="#ff0000">admin</font>**/');  
 define('DIR_WS_CATALOG', '/');  
 define('DIR_WS_HTTPS_ADMIN', '/<font color="#ff0000">**admin**</font>/');  
 define('DIR_WS_HTTPS_CATALOG', '/');  
</pre>

And this section:

<pre> define('DIR_FS_ADMIN', '/home/mystore.com/www/public/<font color="#ff0000">**admin**</font>/');  
 define('DIR_FS_CATALOG', '/home/mystore.com/www/public/');  
</pre>

You will end up with something that looks like this:

<pre> define('DIR_WS_ADMIN', '/<font color="#ff0000">**mysecretadminarea**</font>/');  
 define('DIR_WS_CATALOG', '/');  
 define('DIR_WS_HTTPS_ADMIN', '/<font color="#ff0000">**mysecretadminarea**</font>/');  
 define('DIR_WS_HTTPS_CATALOG', '/');  
</pre>

And:  

<pre> define('DIR_FS_ADMIN', '/home/mystore.com/www/public/<font color="#ff0000">**mysecretadminarea**</font>/');  
 define('DIR_FS_CATALOG', '/home/mystore.com/www/public/');  
</pre>

Now, you must upload the changes back to the server, using your FTP program.  

<font size="4" color="#ff0000">**IMPORTANT NOTE:** Your configure.php file should be set as Read-Only for normal use. So, **you'll need to make it Writable before you'll be able to upload/save your changes** to the file.  (In *some* cases, your server might require you to DELETE the file from your server before you can upload the edited version to replace it.)  
Be sure to make it Read-Only again when finished.  Often you can right-click the file in your FTP program and change the permissions settings there.  There's another FAQ article on how to change file permissions on different hosting servers.</font>  

## B - Rename the Admin folder

Using your FTP software or your webhost's _File Manager_, find your Zen Cart _/admin/_ directory_._ Rename the directory to match the settings you just made in step A.

NOTE: DO NOT advertise this new foldername, else you defeat the entire purpose of renaming it.  And DO NOT EVER put it in your robots.txt file!

## C - Login to your admin using the new URL

To login to your admin system you will now have to visit a new URL that matches the new name used in steps A and B above.  

For example instead of visiting **www.example.com/<u>admin/</u>** visit **http://www.example.com/<u>NeW-NamE4u/</u>**  

_Use of [SSL](http://en.wikipedia.org/wiki/SSL "http://en.wikipedia.org/wiki/SSL") is highly recommended to protect your and your customers information. To enable SSL on your site, see this article:  [http://tutorials.zen-cart.com/index.php?article=14](http://tutorials.zen-cart.com/index.php?article=14)_

## <font color="#000000">D - What if it doesn't work?</font>

If it doesn't work, then you've missed one or more of the steps. <font color="#ff0000">**THE MOST COMMON MISTAKE is ignoring the read-only vs writable alert**</font> in **<font color="#ff0000">BRIGHT RED TEXT</font>** in step A.  
The second most common mistake is changing the WRONG THINGS!  In step A, change ONLY the word "/admin/" in the 3 places shown.
