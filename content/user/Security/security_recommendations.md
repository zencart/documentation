---
title: Security Recommendations
description: Zen Cart Security Recommendations
category: security
weight: 10
---

## SSL Security Protection Tips

Without applying extra efforts to your connection on the internet you are wandering around an unsecured environment. Before you make administrative modifications to secure Zen Cart and its database, you need to equip yourself with secure ways to make these modifications. Otherwise if someone is watching/listing to the information you transmit, it might not be long before your private business information becomes public. The bare minimum you should have is access to shared [SSL](http://en.wikipedia.org/wiki/Secure_Sockets_Layer "http://en.wikipedia.org/wiki/Secure_Sockets_Layer") services from your hosting company.

The preferred would be to have a dedicated SSL certificate for your store, as it is more professional in appearance than the use of a shared certificate. There will be an expense incurred to obtain a dedicated SSL certificate and dedicated IP address in your hosting account.


## Accessing Your Site Files Securely

Instead of using regular FTP to access your server's files, it would be wise (if your hosting company offers FTPS support) to use a program that offers [FTP over SSL/TLS](http://en.wikipedia.org/wiki/FTPS "http://en.wikipedia.org/wiki/FTPS"). This method will encrypt the information you transmit and receive. This is important especially when you are downloading database backups or configuration files which contain usernames and passwords, etc.

If your hosting company does not offer SFTP or FTPS, then they are most likely not PCI Compliant either, and you should be choosing a different hosting company who takes security seriously.

_**The following is a list of several steps you can take to secure your Zen Cart site:**_


## 1\. Remove extra folders from your server after install

It's important that after you've installed your site and are satisfied that it's working properly, including actually doing live transactions to test ALL the payment and shipping modules you're using on your site, be sure to do some cleanup:

REMOVE THE FOLLOWING FOLDERS (and all the files inside them), TO MINIMIZE SECURITY RISKS:

```
 - /docs  
 - /extras  
 - /zc_install  
 - /install.txt (this file can be removed, too)  
```

It is safe to keep these files on your own computer, since they can be used as references/documentation, or used to aid in troubleshooting as diagnostic tools, or for upgrading/installing again in the future. But those folders/files should *not* be on a live webserver.

Optional: Additionally, *IF* you have no intentions of supporting downloadable products or music-media products, you can *also* remove these folders:

```
 - /download  
 - /media  
 - /pub  
```

(And you'll need to go to your Admin->Configuration->Attribute Settings->Enable Downloads, and set it to False to turn off the warning message about the missing download folder) In the future, if you choose to add downloadable products to your site or music-products, you will want to re-upload these appropriate folders (and their contents) to your server again, and assign appropriate permissions.

## 2\. Rename your _/admin_ folder

It is recommended for additional security that you rename your _admin_ directory after installation. This way, it will be significantly harder for hackers to find your admin area or attempt any attack on breaking into it.

[Instructions for renaming your admin folder can be found in this article](/user/running/rename_admin).

If your server doesn't support use of .htaccess files, you'll need to work with your hosting company to come up with a way to provide the security protections offered by the supplied .htaccess files but using *your* server's available tools. If you cannot come up with alternate measures, you should reconsider whether your current hosting service is really adequate for the security appropriate to eCommerce.


## 3\. Use SMTPAUTH or SMTP as your Email Transport method, instead of the generic "PHP" or "sendmail" settings.

Go to Admin->Configuration->Email Options, and change your Email Transport Protocol to SMTPAUTH, and then fill in all the SMTP credentials in the other settings lower on that same screen.

This will not only help prevent outgoing emails from ending up in spam folders, but will also prevent the disclosure of your admin folder when sending emails from your admin screens.


## 4\. Set configure.php files read-only

It's important that you CHMOD (set permissions) on the two configure.php files as <u>**read-only**</u>. Typically this means setting them to _644_, or in some cases _444_.  
The configure.php files are located in:  
/&lt;YOURSITEFOLDER&gt;/includes/configure.php  
/&lt;YOURSITEFOLDER&gt;/renamed-admin/includes/configure.php  

If you're not clear on what YOURSITEFOLDER means, please [read this](/user/first_steps/basic_terms/). 

Quite often setting permissions on a file to read only via FTP will not work. Even if the permission looks like it was set to read only, it really may not have been. You must verify the correct setting by entering the store and seeing if there is a warning message on the top of the screen. "Warning: I am able to write to the configuration file:..." In this case you will need to use the "File Manager" supplied with your webhosting account.

If you're using a Windows server, simply set the file as _Read-Only_ for _Everyone_ and especially the IUSR_xxxxx (Internet Guest Account) user if running IIS, or the _System_ account or _apache user_ if running Apache.


## 5\. Delete any unused _Admin_ accounts

v1.3.x or older:  
Admin > Tools > Admin Settings  
v1.5.0 or newer:  
Admin > Admin Access > Admin Users  

In your admin Users screen, check for any unused Admin accounts, and delete them. Especially the Demo account, if it exists.


## 6\. Admin Password Security

It is wise to use complicated passwords so that a would-be hacker can't easily guess them.

We recommend that you use passwords that are at least eight or more characters long, and a mix of letters and numbers, and even upper-and-lower case. Making it multiple words (of letters-and-numbers) with spaces in between will make it almost impossible to guess or crack.

If you are going to use normal words it is a good idea to join together two normal words that don't normally go together, again separating them with spaces and maybe mixing in some uppercase letters.

Admin passwords should be changed at least every 3 months.

v1.3.9 and older:  
You can change your Admin password in Admin > Tools > Admin Settings, and click on the Reset Password button, or click on the icon that looks like a recycle symbol.  
v1.5.0 and newer:  
Visit Admin > Admin Access > Admin Users to change passwords.


## 7\. Admin Access Protection

It is wise to observe caution while working in your admin area:

- **use only one browser tab** to access your admin area

- **do NOT visit other sites (ESPECIALLY email sites like gmail/yahoo/hotmail/etc) when your browser has an active admin login session enabled -- even in another tab** (this is because if you're clicking links in emails you run the risk of opening yourself up to XSS problems if you're logged into your store admin at the same time. It's like handling raw chicken and licking your fingers ... do so at your own risk!)

- **always log out of your admin** when not using it


## 8\. Protect your "define pages" content in "html_includes"

After you have finished editing your define pages in [Admin > Tools > Define Pages Editor](/user/admin_pages/tools/define_pages/), you should protect them:

A. Download a copy of them to your PC using your FTP software. They are located in the /includes/languages/english/html_includes folder and subfolders.

B. Make them CHMOD 644 (ie: “read-only”). See notes above on CHMOD. `/includes/languages/english/html_includes` – and all files/folders underneath

If you make them read-only, then a would-be hacker cannot edit them if they gain access to your system, unless they can get permissions to change the read-only status, which is more complicated.

Note: Of course, once you set them read-only, then you'll need to go and set them back to read-write before making additional changes using the define-pages editor or uploading replacements via FTP, and then read-only again when done.

## 9\. Use _.htaccess_ files to protect against unwanted snooping

**NOTE: This step is already largely addressed in v1.3.9 and v1.5.0 and newer, with the included .htaccess files. If you are using older versions of Zen Cart then you will have to do these adjustments manually:**

In several folders, there are _.htaccess_ files to prevent malicious visitors from being able to browse through the files on your site unless they know exact filenames. Some also prevent access to any .PHP scripts, since it's expected that all PHP files in those folders will be accessed by other PHP files, and not by a browser directly. This is good for security. If you delete these files, you run the risk of leaving yourself open to people snooping around.

There are also some blank _index.html_ files in several folders. These files are there to protect you in case your FTP software won't upload _.htaccess_ files, or your server won't accept them. These only prevent directory browsing, and do not stop execution of .PHP files. It's a good alternative, although using _.htaccess_ files in all of these folders is the better choice, for servers that accept them.

Suggested content for _.htaccess_ files in folders where there is an _index.html_ file but not yet an _.htaccess_ file would be something like the following (depends on your server configuration):

```
#.htaccess to prevent unauthorized file access files  
  OPTIONS -Indexes -ExecCGI  
  IndexIgnore */*  
  ### This part says to deny access to EVERYTHING. Afterwards, you'll allow access to JUST the permitted items. See next FilesMatch section.  
  <FilesMatch .*>  
   Order Deny,Allow  
   Deny from all  
  </FilesMatch>  
  ### Add only appropriate PERMITTED filetypes to this list, depending on which folder you're protecting:  
  <FilesMatch .*\.(js|css|jpg|gif|png|swf)>  
   Order Deny,Allow  
   Allow from all  
  </FilesMatch></span>  
```

In order for the above suggestions to work, your host must include either 'All' or all of these: 'Limit Options Indexes' parameters to the AllowOverride configuration in the server's master apache httpd.conf file.

If your webhost configuration doesn't allow you to create/use your own _.htaccess_ files, you'll need to work with your hosting company to come up with a way to provide the security protections offered by the supplied .htaccess files but using *your* server's available tools; sometimes they provide an interface in your hosting admin control panel where you can set the desired settings. You need to choose, and use, the appropriate method for your server. As mentioned above, it's best to work with your web hosting company to select and implement the best method for your specific server. We can't tell you what to use for your specific server, but we offer these guidelines as a starting point. If you cannot come up with alternate measures, you should reconsider whether your current hosting service is really adequate for the security appropriate to eCommerce.


## 10\. Protect your "images" and other folders

During initial installation, you are advised to set your images folder to read/write, so that you can use the _Admin_ interface to upload product/category images without having to use FTP for each one. Similar recommendations are made to other files for various reasons.

However, leaving the images (or any other) folder in read/write mode means that hackers might be able to put malicious files in this (or other) folder(s) and thus create access points from which to attempt nasty exploits.

Thus, once your site is built and your images have been created/loaded, you should drop the security down from read/write to read. ie: change from CHMOD 777 down to 644 for files and 755 for folders.

<u>**_(Note: This is already done since v1.3.9)_**</u> -- *IF* your server is running PHP as a CGI application and not as an Apache module, and you wish to prevent hackers from executing scripts in your images folder (which is only an issue *if* they are able to successfully hack to your images folder and insert rogue script files), you could further secure it by adding a custom .htaccess file which only allows images to be displayed, and won't allow the use of php files etc. Here's the code for said custom .htaccess file:

```
# Prevent directory viewing and the ability of any scripts to run.  
 # No script, be it PHP, PERL or whatever, can normally be executed if ExecCGI is disabled.  
 OPTIONS -Indexes -ExecCGI</span>  
``` 

#### File/Folder permissions settings

On Linux/Unix hosts, generally, permission-setting recommendations for basic security are:

*   folders/directories: 755
*   files: 644

On Windows hosts, setting files read-only is usually sufficient. Should double-check that the _Internet Guest Account_ has limited (read-only) access.

#### Folder Purposes

The folders for which installation suggests read-write access for setup are these. If your site supports .htaccess protection, then you should use it for these folders.

*   /**cache**  
    This is used to cache session and database information. The BEST security protection for this is to move it to a folder "above" the public_html/htdocs/www area, so that it's not accessible via a browser. (Requires changes to DIR_FS_SQL_CACHE setting in configure.php files as well as [Admin > Configuration > Sessions > Session Directory](/user/admin_pages/configuration/configuration_sessions).
*   /**images**  
    See other suggestions earlier.
*   /**includes/languages/english/html_includes**  
    See other suggestions earlier.
*   /**logs**  
    This folder is used for storing debug or error logs needed for troubleshooting problems which may be ocurring on your site. You may wish to relocate this folder above your web/document-root for security reasons. Update the DIR_FS_LOG in both configure.php files to point to the new location.  
    (Not applicable to versions older than v1.5.0)
*   /**media**  
    This is only suggested read-write for the sake of being able to upload music-product media files via the admin. Could be done by FTP as an alternative.
*   /**pub**  
    This is used on Linux/Unix hosts to have downloadable products made available to customers via a secure delivery method which doesn't disclose the 'real' location of files/data on your server (so that people can't share a URL and have their friends steal downloads from your site)
*   /**admin/backups**  
    This is used by automated backup routines to store database backups. Optional.
*   /**admin/images/graphs**  
    This is used by the [Admin > Tools > Banner Manager](/user/admin_pages/tools/banner_manager) 
for updating/displaying bar graphs related to banner usage. If not writable, this feature is ignored.


## 11\. Remove the print URL feature from your browser

To stop the browser from printing the admin URL (which discloses your Admin foldername) on the invoice follow these steps:.  

*   Microsoft Internet Explorer  

    *   Click on _File_ then _Page Setup_
    *   At page setup window, remove these two character combination "&u" from the header or footer text box.
*   Firefox  

    *   Click on _File_ then _Page Setup_
    *   On page setup window click on the tab "Margins & Header/Footer". In the "Header & Footer" section set all of the drop downs to --blank--. (Or at least remove all instances of "Title" and "URL" from the various boxes.)
*   Other browsers offer similar menu choices to change these settings.


## 12\. Things to Check Up on Regularly

1.  Be sure you've done all the steps listed in this document.
2.  Make recent backups of your website files and database.
    *   Backup the database over a secure connection (ie: if you're using phpMyAdmin to backup, then make sure you're using HTTPS addresses in your URLs).
    *   Backup the website files over a secure connection (If you're copying files via FTP, be sure to use SECURE-FTP [FTP over SSL/TLS](http://en.wikipedia.org/wiki/FTPS "http://en.wikipedia.org/wiki/FTPS")). A good tool that supports Secure FTP (SFTP) is WinSCP, provided you configure your connection in it accordingly.)
    *   Store the backed up database and website files into an encrypted file. (You should NOT keep your backups on your server. But if you do, encrypt them securely. See your hosting company for advice.)
3.  Check your server's error log regularly for odd or suspicious activity. (Your hosting control panel should give you access to the Apache error_log)
    *   Look for any links that went to a page that isn't in your site.
    *   Look for links that have http after the _index.php_.
4.  Check your website files regularly to be sure nothing's been added or altered.
5.  Ask your web host what they have done to be sure the server you're on is safe and secure so that outsiders cannot do any harm, and so that other websites on your server cannot be used to get to your site and cause any harm (in case they have security holes in them).
6.  If your business warrants, or you still want additional assurance (especially if running forum software on your site, or other scripts outside of Zen Cart), hire a security consultant to check your site regularly and give you peace of mind in exchange for a few dollars.
7.  Check your Zen Cart /logs/ or /cache/ folder for myDebug-XXXXX.log files to see whether any errors are happening which need to be fixed. Delete the log files after you've addressed the errors.

## 13. Server Operating System Patches

There are some common server vulnerabilities that are worth checking into to ensure your server isn't vulnerable to easy hacker exploits. There are entire professions dedicated to this subject, so it's impossible to list everything here; but some of the more common things needing attention are:

1.  SSL Patch: [http://heartbleed.com/](http://heartbleed.com/)
2.  PHP CGI Patch: [http://arstechnica.com/security/2014/03/php-bug-allowing-site-hijacking-still-menaces-internet-22-months-on/](http://arstechnica.com/security/2014/03/php-bug-allowing-site-hijacking-still-menaces-internet-22-months-on/)

