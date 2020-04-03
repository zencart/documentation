---
title: How do I Install Zen Cart?
description: How do I Install Zen Cart?
category: Installing
weight: 10
---

## Preface

The hoster-provided or publicly available **"packaged bundles" of Zen Cart are not endorsed** by Zen-Cart.com.  

Instead, **we recommend manual installation**.  Manual installation of files from the [official download](https://sourceforge.net/projects/zencart/files/) enables you to build a system which is secure, optimized, and up to date. Manual installation ensures that you know *exactly* what *you* have put onto your site.  


This is a basic guide to installing Zen Cart®. If you already have Zen Cart® installed and wish to upgrade from a previous version to this new release, please see the upgrading instructions [in the Release document](https://www.zen-cart.com/docs/). 

---

## A. The Basics

You have downloaded the [official Zen Cart® software](https://sourceforge.net/projects/zencart/files/), and want to build an online shopping cart.

Questions to ask yourself:

### 1\. Do you have a domain and hosting account?

If No, stop, and see our [Certified Hosting](https://www.zen-cart.com/hosting) Sites and find a fast, reliable hosting site that can help you register your own personal domain, as well as provide for your hosting needs that meet the Zen Cart® software requirements.

Not sure what a domain or hosting account is?  [See this article](/user/first_steps/hosting/).

### 2\. Do you have FTP software?

If No, stop.  You need to obtain a good [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to transfer files back and forth from your computer to [your web host](/user/first_steps/hosting/#hosting-companies).

**NOTE:** Many people have had timeout and other problems when using programs like SmartFTP and CuteFTP. We recommend that you do NOT use these problematic programs.  See [FTP tools](/user/first_steps/useful_tools/#ftp-tools) for a list of alternatives. 

**NOTE 2:** If your hosting company provides an FTP program that runs inside your browser, we recommend that you do NOT use that for uploading large amounts of files such as a fresh install of Zen Cart. Those are okay for single-file uploads, but unreliable for several files at once.</span>

**NOTE 3:** While some programs like Dreamweaver have built-in FTP capability, we DO NOT recommend using these programs for uploading more than one file at a time, since they often fail to do mass uploads properly, and do a very poor job of informing you of any failures. Always better to use a program dedicated to FTP activity, and not something that's merely got rudimentary FTP capability bolted on.  

### 3\. Do you have a good Text Editor?

If No stop.  You will need a [text editor](/user/first_steps/useful_tools/#php-html-and-text-editors).

**NOTE:** Do not use cPanel for editing files.

**NOTE:** Do not use MS Word for editing files. 


### 4\. Do you have access to your webhosting control panel?

Your webhoster's control panel (often [cPanel](https://cPanel.net) but sometimes a hoster-built tool) is where you will create a MySQL database and user.

BEFORE YOU PROCEED, make sure you have access to a MySQL database, and username/password to that database. You may need to create the database using your webhosting account's control panel. Contact your webhosting company for assistance. Zen Cart® cannot create the database for you.

(You need the following permissions on your MySQL user: SELECT, INSERT, UPDATE, DELETE, CREATE, ALTER, INDEX, DROP.   On an H-Sphere host, this would be "dba" access, or at least read/write. )  

### All set?

If you have answered Yes to all 4 of these questions, then you are ready to go on. 

### ZIP file

If you're reading this page via a file from your computer, you have likely already unzipped the [Zen Cart® distribution file](https://www.zen-cart.com/getit) and its contents into a folder on your personal computer. If for some reason you haven't already done so, unzip the files to your PC now, retaining the file structure within the zip file.  

---
## B. Upload the Zen Cart® fileset to your webserver

Upload, via FTP, the whole program into a directory on your server.  You can put it in your webroot or in a folder below that. 
  
### What is my webroot? 

Each web host has his/her own preference in naming folders for use in running a website.  
You can have many files that don't even get shown to the public. The ones that are available for access via a browser are usually in a folder called something like:

- `/home/YOURNAME/public_html`
or  
- `/var/www/YOURNAME/httpdocs`
or  
- `/usr/accounts/a/b/YOURNAME/httpd`

etc.

Basically, in your FTP area look for a `www` or `public_html` or `htdocs` or `httpdocs` or `wwwroot` folder. These are the common folder names for what is referred to as the **webroot**, which is where all website content is served from.  

Your Zen Cart files (or *any* files to run your website, for that matter) need to be under that folder. If they're not, then you're going to get "not found" errors - because the content is not found!

If it's unclear where the publicly-accessible files are to be uploaded, ask your hosting company for assistance in determining what your **webroot** folder should be.

### What folder do I upload into?

You can choose to upload to your webroot, or you can choose to upload to a subfolder.  Assuming your webroot is `/home/johndoe/public_html` and your domain is `johndoetools`, this is how things will work (assuming you have SSL): 

- If you upload to your webroot, your Zen Cart will be accessed as [https://www.johndoetools.com]().

- If you upload to the catalog subfolder of your webroot (i.e. `/home/johndoe/public_html/catalog/`, your Zen Cart will be accessed as [https://www.johndoetools.com/catalog]().

This guide uses the `/catalog` subfolder AS AN EXAMPLE.   You don't have to use `/catalog`.  You could use something else (like `/shop`), or no subfolder at all (upload directly to webroot). 

So in the language defined by [Basic Terms](/user/first_steps/basic_terms), we'll
be using a `YOURSUBFOLDER` value of `/catalog/`.

Choosing a subfolder versus loading the files into webroot is entirely your 
choice.  The only time when you would really need to use a subfolder is if you
already have a well established website are just adding on ecommerce using 
Zen Cart.  In that case, you'd want to put your store below your existing site. 


---
## C. Create the configure.php files

Two files need to be created on the server. These are the configure.php files that identify the settings of your particular server and the location of the files that you just loaded. After they have been created, you will then need to change the permissions on these files.  

**NOTE:** Changing permissions can be done via your FTP program with the chmod feature. Usually clicking right on a directory or filename will open a menu with this option (perhaps under "Properties")  

On the server locate the file: `/catalog/includes/dist-configure.php`  
Rename this file to `configure.php` and change the permissions to 777 (read-write-execute for all)  

Next, on the server locate the file: `/catalog/admin/includes/dist-configure.php`  
Rename this file to `configure.php` and change the permissions to 777 (read-write-execute for all)  

**NOTE FOR IIS USERS:** If you are using IIS for Windows hosting, the "chmod 777" idea for permissions settings is likely foreign to you. In IIS, under Windows, you need to right-click on the file (or folders in the next section below), and choose Properties. Then under the Security tab, ensure that the"**Internet Guest Account**", identified usually as: `MACHINE_NAME\IUSR_MACHINE_NAME` has at least "read" and "write" privileges.  It is likely best to give "modify" as well. This should be done on each file/folder indicated. (If the `IUSR_MACHINE_NAME` account isn't listed, click "Add" and add that account from the list, and then set the required permissions.) (Note: `_MACHINE_NAME` above refers to the "machine name" or "computer name" configured by the server administrator to "name" the server.)  

**NOTE FOR IIS USERS:** Stop. Get Linux hosting.  IIS is not recommended. 

--- 
## D. Set Permissions on folders

When you upload files to your server, the server will automatically set certain default permissions on those files and folders. Typically folders are set to 755 and files are set to 644\. Most servers use these values. Yours may or may not.  

Some folders and files need special "writable" permissions for use in Zen Cart. "Writable" typically requires 777 permission. (Your hosting company may only allow 755 as writable, and using 777 may cause blank screens when accessing your site. In that case, use 755. Ask your hosting company for direction.)  

As such, you need to change the permissions on the following directories to 777 (read/write/execute). If your program allows you to set these permissions "recursively", choose that option.  

```
*   /catalog/cache
*   /catalog/images
*   /catalog/includes/languages/english/html_includes
*   /catalog/media
*   /catalog/pub
*   /catalog/admin/backups
*   /catalog/admin/images/graphs
```

Note: open the catalog/images directory and change **all** of the subdirectories and their subdirectories to 777 as well. For example (this is a partial list):  

```
*   /catalog/images/attributes
*   /catalog/images/banners
*   /catalog/images/categories
*   /catalog/images/large
*   /catalog/images/large/dvd
*   /catalog/images/manufacturers
*   /catalog/images/medium
*   /catalog/images/upload
```

**NOTE:** If you miss any of the images directories and subdirectories inside 
`/images` and try to use them later, you will get an error message that you cannot write to these directories.  

As for other files, they can be CHMOD 644, or 444, depending on your webserver configuration.  Folders don't usually get set below 755.  


--- 
## E. Prepare to Run the Installer

The installer is fairly intelligent and should be able to automatically supply answers to the questions listed below.  

You will, however, need to confirm that the auto-detected answers are, in fact, correct as on some servers they may differ.  

You will need the following information for the installation:  

*   **The physical path to your new Zen Cart® directory**  
    Example: `/home/myusername/public_html/catalog`  

*   **The Virtual HTTP Path (the URL to your domain and directory for your shop)**  
    Example: `http://www.mydomain.com/catalog` 

*   **The Virtual HTTPS Server (the secure URL to your domain)**  
    Example: `https://www.mydomain.com`
    Note: if you have a shared certificate on a virtual server this may look like:  
    `https://mydomain.secureservername.net/`  
    - or - `https://secure.sharedservername.net/~username`  

*   **The Virtual HTTPS Path (the secure URL to your domain and directory for your shop)**  
    Example: `https://www.mydomain.com/catalog`
    - or - `https://secure.sharedservername.net/~username/catalog`

--- 
## F. Run the Installer

In your browser, enter the URL to your new shop, and the Installer should automatically start.  
Example: `http://www.mydomain.com/catalog`
- or - to start the installer directly, use: `http://www.mydomain.com/catalog/zc_install`

If you now see a list of filenames and directories, you should speak to your Hosting Site about how to setup your server to auto-detect PHP filename extensions.  

### Welcome

You will be presented with a "Welcome to Zen Cart®" page, explaining the features of Zen Cart®.  

### License

Clicking on Continue takes you to the license screen where you are asked to read and confirm acceptance of the GPL licensing agreement.  

### System Inspection

Next, it will examine your server for compliance with technical requirements for running Zen Cart®, presenting you with several items you may need or want to address with your host. Anything marked in red or with an "X" must be addressed before the installer can continue. Things marked with an orange or yellow "caution" symbol are simply warnings that may or may not apply to your setup now. The image folders and others as described earlier in this document are also noted. If you make changes to your server, you can click Re-Check or press F5 in your browser to refresh the display and reflect the changes you've made before proceeding.  

If a previous version of Zen Cart® is found on your server, the installer will attempt to determine the database patch level and display that on the screen as well. In this case, an "upgrade" button will display at the bottom of the screen offering you the ability to upgrade if needed. 

Once you are satisfied that the "pre-flight-check" inspection is OK for your needs (ideally, all green check-marks), you may click the "Install" button at the bottom of the screen.  

### System Setup

On the System Setup page you will need to complete the information we described in "Before Running the Installer" earlier in this document.  

Indicate if you want to Enable SSL (the secure pages where required, in Login, Checkout, and optionally Admin areas) on your server. If you do not have an SSL certificate yet, **do not enable this feature now**.It can be changed at a later date. (See the [SSL FAQ](/user/installing/enable_ssl) for detailed instructions).  

Note: If you receive any of the following error messages, go through the above steps to make sure you have not left anything out. All error messages have context-sensitive help via a popup window if you click on the <span class="pseudolink">more info...</span> links supplied:  

    ** Warning: Problems Found **  
    *   /includes/configure.php does not exist.  more info... 
    *   /admin/includes/configure.php does not exist.  more info...  
 


### Database Setup

On the next screen, you are asked for Database Information about your MySQL database, username and password. These can be obtained from your cPanel or equivalent control screen provided by your host. If you do not have a clean MySQL database setup with a username and password, you will need to create one.

Contact your Hosting site if you need assistance in creating a MySQL database table and/or username and password. **Note that you need to have your database and userID created before the Zen Cart® installer can continue past this screen**.  

Other information on this screen:

*   At this time, MySQL is the primary operational database type.  
    Future releases may support other database types.  

*   We recommend that you store your Database Sessions in your database for security purposes.

### Store Setup

Now, complete the Store Information about your Shop.  

Note: except for "demo data", all of the information here can be (re)configured later in the Admin area of your shop.  

### Demo Data       
If you would like to install the demo data, select yes.  

We recommend that you install the demo data to familiarize yourself with many of the examples created that explain and demonstrate the vast number of features available in Zen Cart®.  

You may also decide later to set up a test site with the demo data AND a separate working site for your live data so that you have the ability to refer back to the demo data for help and to see examples of a feature.  This is an excellent way to learn how things work, and then try your hand at setting up your own site and testing to be sure you've done things right. Later on it can be used to help you test an upgrade or test new features you're working on before affecting your live site.  

After you click Save Store Settings, there will be some hesitation as the database tables are created and the demo data is optionally loaded. You will see some progress indicators as the database is loaded.  

### Admin Setup

Now, complete the Admin Information to set your Login name, Admin email address and password.  

**NOTE:** both the login name and password are case sensitive.  

Save the Admin settings and your installation is now complete!  

Providing there were no errors during installation, you should be able to now enter the Admin or the Catalog.  

---
## G. After Installation

a) [RENAME YOUR ADMIN FOLDER](/user/running/rename_admin/).  Note that 
current versions of Zen Cart do this for you. 

b) When you enter the catalog, you will receive security warnings about the `configure.php` files and the `/zc_install` directory.  

**configure.php files**  

You will now want to change the permissions on the configure.php files with `chmod 644` (or 444 depending on your server, and sometimes setting 444 cannot be done via FTP, in which case use your host's control panel or file manager to set the permissions level.)  

These are located here (remember, "catalog" is what we used as an example here -- your site may or may not include "catalog" as a folder name):  


    /catalog/includes/configure.php
    /catalog/admin/includes/configure.php


It would also be a good idea to download a copy of these files to your computer from the server as they have been setup and configured to your server specifications based on the Installation process.  

If you have any errors or problems, most of these can be corrected by minor adjustments to these two files.  

c) Remove the **zc_install directory**  
Next, you will want to delete the `/catalog/zc_install` directory  

---
## H. Next Steps

Now you'll want to [install your SSL certificate](/user/installing/enable_ssl/) and change your admin password.  [Yes, you need an SSL certificate](/user/first_steps/yes_you_need_ssl). 

For information on first steps to setting up your online shop, see the article [basic checklist](/user/first_steps/basic_checklist/). 

You should also familiarize yourself with the Zen Cart® [Developer's Toolkit](/user/admin/developers_toolkit), located in your store's Admin area, under `Tools`. This will help you locate almost anything you want to customize in your shop!

Once you're set up and ready to start announcing your URL to the public, you should FIRST review Site Security Recommendations to be sure your site is safe and not vulnerable to hackers. The most up-to-date version of this file can be found in the article [Important Security Recommendations](https://www.zen-cart.com/docs/important_site_security_recommendations.html). 


