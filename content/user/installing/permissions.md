---
title: Permissions on files and folders 
description: What access levels should be used?
category: installing 
weight: 10
---

FIXME - please review 

**NOTE:** While the following instructions talk about making files/folders writable, it is wise to review your security settings after installation to be sure you're not leaving yourself open to hacking vulnerability by having too many "world-writable" files on your site.  
There are [detailed security recommendations on this topic](/user/security/security_recommendations/).

## Using FTP 

You will be using your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to do this.

Most FTP programs will allow you to change file permissions.

Connect to your site with your FTP program.

Move to your `public_html` directory. 

If you have installed your cart in a [subfolder](/user/installing/subfolder/), move to that folder. Some common subfolder names are `store`, `shop` or `cart`. 

Then look for a "Properties" command that can be applied to that directory (often if you right click, Properties will be one of the options).

Then change the permissions to the needed setting for the following folders:

If prompted whether to include files/folders underneath them (also called "recursive"), say or check "Yes"

All of these folders to "writable" (often this means 755).

(Specifically, these need to be writable so that files can be uploaded to them, or created in them or written to them by PHP.)

```
*   /cache
*   /images
*   /includes/languages/english/html_includes
*   /media
*   /pub
*   /admin/backups
*   /admin/images/graphs
*   /zc_install/includes/nginx_conf
```

### Using cPanel

In cPanel, you have File Manager.

Open File Manager, and browse to the folder where you have put your Zen Cart files, and make the changes to particular files/folders as needed.

Example: /includes/languages/english/html_includes  

Browse down through  

- includes  
- languages  
- english  
- html_includes  

Click on html_includes.  

Then you'll get another page, and likely in the top right corner there will be a "folder permissions" or "permissions" link. Click on that.  

Then set the permissions to read, write, and execute for ALL categories of users (usually 9 checkboxes). If it has an option to process all files under this subdirectory, check that box. Then click OK (or whatever button to process the changes).  

### Using SSH

If you have SSH access instead of cPanel, you could type the following commands:  

```
chdir /home/myaccount/public_html/zencart
```

(substitute your actual working directory)  

Type the following commands in the case shown: 

```
chmod -R 755 ./logs
chmod -R 755 ./cache
chmod -R 755 ./pub
chmod -R 755 ./images
chmod -R 755 ./includes/languages/english/html_includes
chmod -R 755 ./admin/backups
chmod -R 755 ./zc_install/includes/nginx_conf
```


**OPTIONAL:** And this line changes all the files (not folders) and files within subfolders (but not the folders themselves) to be ideal for typical webserver use:

```
find ./ -type f -exec chmod 644 {} \;
```

If these methods don't work, then you'll need to contact your hosting company for assistance in changing file permissions.

## Additional Permissions to Set 

Using which ever method you used above, you also need to make the following 
permission changes: 

### Images 
Open the `/images` directory and change **all** of the subdirectories and their subdirectories to 755 as well. For example (this is a partial list):  

```
*   /images/attributes
*   /images/banners
*   /images/categories
*   /images/large
*   /images/large/dvd
*   /images/manufacturers
*   /images/medium
*   /images/upload
```

**NOTE:** If you miss any of the images directories and subdirectories inside 
`/images` and try to use them later, you will get an error message that you cannot write to these directories.  

As for other files, they can be CHMOD 644, or 444, depending on your webserver configuration.  Folders don't usually get set below 755.  


