---
title: Security Recommendations
description: Running your site securely
category: security
weight: 10
---

## Security basics

- Learn about [running your site securely](/user/first_steps/security/).

- Get an [SSL certificate](/user/installing/enable_ssl/). Yes, [you need SSL](/user/first_steps/yes_you_need_ssl/). 

## Steps to a More Secure Site

### 1\. Remove extra folders from your server after install

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

Then you'll need to go to your Admin > Configuration > Attribute Settings > Enable Downloads, and set it to _False_ to turn off the warning message about the missing download folder. 

In the future, if you choose to add downloadable products to your site or music-products, you will want to re-upload these appropriate folders (and their contents) to your server again, and assign appropriate permissions.

### 2\. _/admin_ folder name

It is recommended for additional security that you not use `admin` as the name of your Admin area. This way, it will be significantly harder for hackers to find your admin area or attempt any attack on breaking into it.

By default the Zen Cart installer will rename it for you. 

Some 3rd-party auto-install scripts provided by hosting companies also use a directory not called "admin" ... but they always use the same directory name on all sites they install, so you really ought to rename it yourself!!!

[Instructions for renaming your admin folder can be found in this article](/user/installing/rename_admin/).


### 3\. Use SMTPAUTH or SMTP as your Email Transport method, instead of the generic "PHP" or "sendmail" settings.

Go to Admin > Configuration > Email, and change your Email Transport Protocol to SMTPAUTH, and then fill in all the SMTP credentials in the other settings lower on that same screen.

This will not only help prevent outgoing emails from ending up in spam folders, but will also prevent the disclosure of your admin folder when sending emails from your admin screens.


### 4\. Block bad guys as needed 

Depending on the amount of bad traffic you get, you may need to look at solutions like Cloudflare, cpHulk, Access Blocker, Config Server Firewall, etc. 

Please see [blocking attacks](/user/troubleshooting/blocking_attacks/) for more details. 

### 5\. Delete any unused _Admin_ accounts

Go to: Admin > Admin Access > Admin Users  

In your admin Users screen, check for any unused/unrecognized Admin accounts, and delete them. Especially the Demo account, if it exists.


### 6\. Admin Password Security

It is wise to use complicated passwords so that a would-be hacker can't easily guess them.

We recommend that you use passwords that are at least eight or more characters long, and a mix of letters and numbers, and even upper-and-lower case. Making it multiple words (of letters-and-numbers) with spaces in between will make it almost impossible to guess or crack.

If you are going to use normal words it is a good idea to join together two normal words that don't normally go together, again separating them with spaces and maybe mixing in some uppercase letters.

Admin passwords should be changed at least every 3 months. And anytime an employee leaves your company.

Visit Admin > Admin Access > Admin Users to change passwords.

(or for v1.3.9 and older, you can change your Admin password in Admin > Tools > Admin Settings, and click on the Reset Password button, or click on the icon that looks like a recycle symbol.)


### 7\. Admin Access Protection

It is wise to observe caution while working in your admin area:

- **use only one browser tab** to access your admin area

- **always log out of your admin** when not using it

Be careful clicking on links in emails whose content/purpose you don't recognize/expect. 


### 8\. Protect your "define pages" content in "html_includes"

After you have finished editing your define pages in [Admin > Tools > Define Pages Editor](/user/admin_pages/tools/define_pages/), you should protect them:

A. Download a copy of them to your PC using your [FTP software](/user/first_steps/useful_tools/). They are located in the `/includes/languages/english/html_includes` folder and subfolders.

B. Make them read-only. See notes above on CHMOD. 

`/includes/languages/english/html_includes` – and all files/folders underneath

If you make them read-only, then a would-be hacker cannot edit them if they gain access to your system, unless they can get permissions to change the read-only status, which is more complicated.

Note: Of course, once you set them read-only, then you'll need to go and set them back to read-write before making additional changes using the define-pages editor or uploading replacements via FTP, and then read-only again when done.

### 9\. Use _.htaccess_ files to protect against unwanted snooping

If your server doesn't support use of .htaccess files, you'll need to work with your hosting company to come up with a way to provide the security protections offered by the supplied `.htaccess` files but using *your* server's available tools. If you cannot come up with alternate measures, you should reconsider whether your current hosting service is really adequate for the security appropriate to eCommerce.

In order for the `.htaccess` protections to work effectively, your host must include either `All` or all of these: `Limit Options Indexes` parameters to the `AllowOverride` configuration in the server's master Apache `httpd.conf` file.


### 10\. Protect your "images" and other folders

During initial installation, you are advised to set your images folder to read/write, so that you can use the _Admin_ interface to upload product/category images without having to use FTP for each one. Similar recommendations are made to other files for various reasons.

However, leaving the images (or any other) folder in read/write mode means that hackers might be able to put malicious files in this (or other) folder(s) and thus create access points from which to attempt nasty exploits.

Thus, once your site is built and your images have been created/loaded, you could drop the security for the images directories down from read/write to read-only. ie: chmod down to 644 for files and 755 for folders.


#### File/Folder permissions settings

On Linux/Unix hosts, generally, permission-setting recommendations for basic security are:

*   folders/directories: 755
*   files: 644

On Windows hosts, setting files read-only is usually sufficient. Should double-check that the _Internet Guest Account_ has limited (read-only) access.

#### Folder Purposes

The folders for which installation suggests read-write access for setup are these. If your site supports .htaccess protection, then you should use it for these folders.

*   /**cache**  
    This is used to cache session and database information. The BEST security protection for this is to move it to a folder "above" the 
 [webroot](/user/first_steps/how_do_i_install#what-is-my-webroot) 
so that it's not accessible via a browser. (Requires changes to `DIR_FS_SQL_CACHE` setting in configure.php files as well as [Admin > Configuration > Sessions > Session Directory](/user/admin_pages/configuration/configuration_sessions/).
*   /**images**  
    See other suggestions earlier.
*   /**includes/languages/english/html_includes**  
    See other suggestions earlier.
*   /**logs**  
    This folder is used for storing debug or error logs needed for troubleshooting problems which may be occurring on your site. You may wish to relocate this folder above your web/document-root for security reasons. Update the DIR_FS_LOG in both configure.php files to point to the new location.  
    (Not applicable to versions older than v1.5.0)
*   /**media**  
    This is only suggested read-write for the sake of being able to upload music-product media files via the admin. Could be done by FTP as an alternative.
*   /**pub**  
    This is used on Linux/Unix hosts to have downloadable products made available to customers via a secure delivery method which doesn't disclose the 'real' location of files/data on your server (so that people can't share a URL and have their friends steal downloads from your site)
*   /**admin/backups**  
    This is used by automated backup routines to store database backups. Optional.
*   /**admin/images/graphs**  
    This is used by the [Admin > Tools > Banner Manager](/user/admin_pages/tools/banner_manager/) 
for updating/displaying bar graphs related to banner usage. If not writable, this feature is ignored.


### 11\. Remove the print URL feature from your browser

To stop the browser from printing the admin URL (which discloses your Admin foldername) on the invoice follow these steps:.  
    *   Click on _File_ then _Page Setup_
    *   On the Page Setup window click on the tab "Margins & Header/Footer". In the "Header & Footer" section set all of the drop downs to --blank--. (Or at least remove all instances of "Title" and "URL" from the various boxes.) (In some browsers the "URL" is denoted by the `&u` pattern, which is what you should remove.)


### 12\. Things to Check Up on Regularly

1.  Be sure you've done all the steps listed in this document.
2.  Make recent backups of your website files and database.
    *   Backup the database over a secure connection (ie: if you're using phpMyAdmin to backup, then make sure you're using HTTPS addresses in your URLs).
    *   Backup the website files over a secure connection If you're copying files via FTP, be sure to use a secure form of FTP, not plain FTP. 
See [FTP tools](/user/first_steps/useful_tools/#ftp-tools) and [security](/user/first_steps/security/).  

    *   Store the backed up database and website files into an encrypted file. Note: You should NOT keep your backups on your server. But if you do, encrypt them securely. See your hosting company for advice.
3.  Check your server's error log regularly for odd or suspicious activity. Your hosting control panel should give you access to the Apache `error_log`.
    *   Look for any links that went to a page that isn't in your site.
    *   Look for links that have `http` after the _index.php_.
4.  Check your website files regularly to be sure nothing's been added or altered.
5.  Ask your web host what they have done to be sure the server you're on is safe and secure.  You need to guard against two things: 
    * Ensure that outsiders cannot cause harm, and 
    * Ensure that other websites on your server with security issues cannot be used to get to your site and cause harm.
6.  If your business warrants, or you still want additional assurance (especially if running forum software on your site, or other scripts outside of Zen Cart), hire a security consultant to check your site regularly and give you peace of mind in exchange for a few dollars.
7.  Check your Zen Cart /logs/ or /cache/ folder for myDEBUG-XXXXX.log files to see whether any errors are happening which need to be fixed. Delete the log files after you've addressed the errors.  If you are not sure how to read log files, see [reading a myDEBUG log](/user/troubleshooting/debug_logs/). 
8.   Ensure your [JavaScript libraries are up to date](/user/upgrading/javascript_updates/) using a tool like Google Lighthouse. 

### 13. Server Operating System Patches

There are some common server vulnerabilities that are worth checking into to ensure your server isn't vulnerable to easy hacker exploits. There are entire professions dedicated to this subject, so it's impossible to list everything here. Work with your hosting company to ensure your server is patched with the latest requirements for your operating system.

### 14. HTTP Headers for PCI Compliance

PCI Compliance aims to provide a secure experience for both you and your customers.
It is common for PCI scanners to flag concerns about same-origin, CSP, XSS, and more. 
To implement these headers in Apache the following `.htaccess` directives could be added to a `.htaccess` file in your site's `document root` (generally `public_html`). Work with your hosting company for specifics, and consult them on how best to customize these to your unique needs. It is important that your `https` configuration is already solid before you implement these; again, work with your hosting company.

```
# Security Headers
<IfModule mod_headers.c>
	Header set X-XSS-Protection "1; mode=block"
	Header set X-Frame-Options "SAMEORIGIN"
	Header set X-Content-Type-Options "nosniff"
	Header always set Strict-Transport-Security "max-age=3000; includeSubDomains"
	# Header set Content-Security-Policy ... # site-owner needs to decide what suits here
	Header set Referrer-Policy "same-origin"
	Header set Feature-Policy "geolocation 'self'; vibrate 'none'"
	Header set X-Permitted-Cross-Domain-Policies: none
</IfModule>
```

### 15. Securing Your Backups

First: You should be [making backups](/user/running/backup/) regularly!

Store your backups someplace for safekeeping. Consider a thumb-drive that you keep with your financial records. The backup can also serve as a snapshot for your data if you need to look back for reference.

While backups are good, too many is bad! ... if they're not secured.

You should only keep backups that are essential for business recovery or financial/business-reference purposes. Keeping too many backups in too many places that are not monitored for privacy can lead to bad situations.

(Consider: you wouldn't leave customers' credit card details in papers laying all over your file cabinets and cupboards and drawers: you'd put them in one central safe spot. Do the same with your backups, and destroy copies that don't need to be kept. This includes not leaving thumb-drives with private data on them sitting around unaccounted-for. Put the important ones someplace safe, and delete the ones that no longer have a purpose.)

