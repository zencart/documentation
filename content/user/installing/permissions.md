---
title: Permissions on files and folders 
description: Permissions on files and folders in Zen Cart
category: installing 
weight: 10
---

**NOTE:** While the following instructions talk about making files/folders writable, it is wise to review your security settings after installation to be sure you're not leaving yourself open to hacking vulnerability by having too many "world-writable" files on your site.  
There are [detailed security recommendations on this topic](/user/security/security_recommendations/).

### How To Set File/Folder Permissions

You will be using your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to do this.

<font color="#3E3E3E">Most FTP programs will allow you to change file permissions.</font>  

<font color="#3E3E3E">Connect to your site with your FTP program.</font>  
<font color="#3E3E3E">Move to your public_html directory, and perhaps into your "zencart" folder underneath public_html, if you've used a subfolder.</font>  

<font color="#3E3E3E">Then look for a "Properties" command that can be applied to that directory (often if you right click, Properties will be one of the options).</font>  
<font color="#3E3E3E">Then change the permissions to the needed setting for the following folders:</font>  
<font color="#3E3E3E">(If prompted whether to include files/folders underneath them (also called "recursive"), say or check "Yes")</font>  

<font color="#3E3E3E">All of these folders to "writable" (often this means 755,</font> 

<font color="#3E3E3E">(Specifically, these need to be writable so that files can be uploaded to them, or created in them or written to them by PHP.)</font>  

*   /logs
*   /cache
*   /pub
*   /images
*   /includes/languages/english/html_includes
*   /admin/backups
*   /admin/images/graphs

### Using cPanel

<font color="#3E3E3E">In cPanel, you have File Manager.</font>  

<font color="#3E3E3E">Open File Manager, and browse to the folder where you have put your Zen Cart files, and make the changes to particular files/folders as needed.</font>  

<font color="#3E3E3E">Example: /includes/languages/english/html_includes</font>  

<font color="#3E3E3E">Browse down through</font>  
<font color="#3E3E3E">- includes</font>  
<font color="#3E3E3E">- languages</font>  
<font color="#3E3E3E">- english</font>  
<font color="#3E3E3E">- html_includes</font>  

<font color="#3E3E3E">Click on html_includes.</font>  

<font color="#3E3E3E">Then you'll get another page, and likely in the top right corner there will be a "folder permissions" or "permissions" link. Click on that.</font>  
<font color="#3E3E3E">Then set the permissions to read, write, and execute for ALL categories of users (usually 9 checkboxes). If it has an option to process all files under this subdirectory, check that box. Then click OK (or whatever button to process the changes).</font>  

### Using SSH

<font color="#3E3E3E">If you have SSH access instead of cPanel, you could type the following commands:</font>  

```
chdir /home/myaccount/public_html/zencart
```

<font color="#3E3E3E">(substitute your actual working directory)</font>  

<font color="#0000ff">Type the following commands:</font>  
<font color="#3E3E3E">(uppercase R is important)</font>  
<font color="#3E3E3E">(If you're running suPHP, then 755 is appropriate, meaning you can probably skip the "777" lines since your folders are probably already 755:</font>


```
chmod -R 777 ./logs
chmod -R 777 ./cache
chmod -R 777 ./pub
chmod -R 777 ./images
chmod -R 777 ./includes/languages/english/html_includes
chmod -R 777 ./admin/backups
chmod -R 777 ./admin/images/graphs
```


**OPTIONAL:** And this line changes all the files (not folders) and files within subfolders (but not the folders themselves) to be ideal for typical webserver use:</font>  

```
find ./ -type f -exec chmod 644 {} \;
```


If these methods don't work, then you'll need to contact your hosting company for assistance in changing file permissions.

### On a Windows Server:

<font color="#3E3E3E">1\. Browse to the wwwroot folder (or whatever path your zen files are in.</font>  
<font color="#3E3E3E">2\. Right-click on a particular file or folder (see list of folders and files above)</font>  
<font color="#3E3E3E">3\. Choose properties</font>  
<font color="#3E3E3E">4\. Choose the Security tab</font>  
<font color="#3E3E3E">5\. Add "IUSR_xxxxxxx" and give read/write permissions to it.</font>  
<font color="#3E3E3E">6\. OK, OK, OK</font>  
<font color="#3E3E3E">7\. If you don't have a "security" tab in step 4 above, simply check the "read" and "write" boxes (or uncheck a read-only box if it exists).</font>  
<font color="#3E3E3E">8\. Repeat for all required files/folders. Same list as for Linux/Unix servers earlier in this FAQ.</font>  

### **On a Windows PC** (sometimes referred to as "localhost"):

<font color="#3E3E3E">Similar to Windows Server above:</font>  
<font color="#3E3E3E">1\. Browse to the wwwroot folder (or whatever path your zen files are in.</font>  
<font color="#3E3E3E">2\. Right-click on a particular file or folder (see list of folders and files above)</font>  
<font color="#3E3E3E">3\. Choose properties</font>  
<font color="#3E3E3E">4\. Set the read-only flag on or off depending on your requirements</font>  
<font color="#3E3E3E">5\. Click Apply and/or OK.</font>  
<font color="#3E3E3E">6\. Repeat for all required files/folders. Same list as for Linux/Unix servers earlier in this FAQ.</font>  

## CONSIDERATIONS WHEN RUNNING suPHP or suExec ON YOUR SERVER:

<font color="#3E3E3E">If your host is running suPHP (occasionally also referred to as suexec), there are a couple variations on permissions issues which you must observe:</font>  
<font color="#3E3E3E">a) you will need to make sure that your files and folders are owned by your username and not root</font>  
<font color="#3E3E3E">b) you also need to make sure that any **folder** that has .php files in it is set to no higher than 755 and .php **files** are set to no higher than 644.  
If either of these is not done, then you'll get "500 Internal Server Error" messages.  
</font>  

Thus, in suPHP mode, substitute "755" for all "777" suggestions mentioned above in relation to *folders*, and "644". Or, if your hosting company has an even stricter configuration, then use the lower numbers specified by them.
