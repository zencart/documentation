---
title: Miscellaneous Troubleshooting Questions
description: Troubleshooting Zen Cart 
category: troubleshooting 
weight: -1 
---

{{< misc >}} 

--- 

### I can't login to the Admin after installing Zen Cart
In most cases of difficulties logging in to the Admin area, the problem is one of:

1.  Admin pages won't show at all, or show without styling.  
    In this case, try temporarily renaming the `admin/.htaccess` file to `htaccess_bak` to see if things operate differently.  
    If they do, then you need to work with your webhost to find the right way to use the supplied `.htaccess` security protections on your site.  

2.  Something may be wrong with the way your site is configured to handle PHP sessions. This is more difficult to resolve.  

    1.  Start by **clearing your browser cache and clearing all cookies**. ** THIS IS THE MOST COMMON PROBLEM **
    2.  Make sure you're not using "Private Browsing" or "Incognito" mode.  

    3.  Then check to be sure that you do NOT have any software **firewall applications** running on your PC, as they may have been set to "disable session cookies".  

    4.  Also, make sure your browser IS **allowed to accept cookies**, esp from your own domain. Cookie-blocking will break your Admin area.  

    5.  Check your **server's errorlog** to determine if any errors are occurring at the time of the failure to login.

    6.  If you are using `www.` in your URL on one page and *not* using `www`  in the URL on another page, you may have problems. This related FAQ may help: [how can I force www?](/user/miscellaneous/force_www/) 

    7.  Try the suggestions in this related FAQ article: [http://tutorials.zen-cart.com/index.php?article=281](http://tutorials.zen-cart.com/index.php?article=281)  

3.  Apart from browser cache and cookies problems, the most common problem is not having the `https` correct in your `admin/includes/configure.php`  file.  
    See: [How do I enable SSL?](/user/installing/enable_ssl/)

4.  If your admin password has been forgotten, or if you've done an admin password reset but forgot what the new password was, you'll have to reset the password via the database. See the FAQ for [resetting the Admin password to default](/user/troubleshooting/reset_admin_password/). 
5.  If you've installed your site into a folder whose name contains spaces, rename the folder so that it doesn't have spaces anymore. Update your `configure.php` files accordingly.

--- 
### 0 DB_ERROR_NOT_CONNECTED
`DB_ERROR_NOT_CONNECTED` occurs when something is wrong with your database.

Possible Causes: 

1. Your `/includes/configure.php` and `/admin/includes/configure.php` files contain settings for the database (`DB_SERVER`
`DB_SERVER_USERNAME`, `DB_SERVER_PASSWORD`, `DB_DATABASE`, `DB_PREFIX`), which are used to log in to the database.

    The `0 DB_ERROR_NOT_CONNECTED` error occurs when those database settings no longer match the actual details for the MySQL server, the MySQL database, or the MySQL user+password, or if the database server is broken for some reason.

    Or, if you recently changed your MySQL user/database/password and didn't put those same changes into your `configure.php` files, you'll need to update your `configure.php` files to match what's required by your MySQL database server. 

2. Some frequently updated tables (such as `sessions` or `whos_online` 
can become corrupt, and cause this problem.  Run a "repair" on the database. Most hosts have a Database Repair option listed beside the database names in the webhosting control panel. Ask your host if you need help finding this.

3. Talk to your hosting company to determine whether they are doing some sort of maintenance on the database.  Tell them that your website cannot connect to your MySQL database, and ask them for some assistance in getting that working again.

--- 
### Where do I find my server's errorlog to review server-side problems?
Your hosting company typically provides this via their control panel.

- If you use cPanel, simply log into your cPanel admin, and click on the Errorlog button.
- Other hosting systems may have the button elsewhere under admin tools
- H-Sphere customers may have to enable errorlog support before it's available.
- Some hosts don't offer it via the control panel; they may offer it via a `/logs` folder instead.  Note that this is not your Zen Cart `/logs` folder - it's a above your webroot at the top of your hosting account folder. 
---
### Error 2006 MySQL server has gone away or 2013 Lost connection to MySQL server during query
"MySQL server has gone away" means that when you clicked on something to ask Zen Cart to do something, it started processing the request, but when it went to retrieve data from the database, it found that the database connection had disconnected, but not by Zen Cart's request.

Possible causes: 
- slow connection to external systems being accessed to produce part of page contents (e.g.: a USPS shipping quote when USPS servers are running slow)
- your own webserver is running slow (perhaps due to bogged down processing while the server is handling a bunch of spam email, or if your server is overloaded because your hosting company has too many customers on the one server)
- your hosting company may have configured the server to expire database connections on a very short time period. Most hosts allow connections to remain open for 30 seconds or more, depending on how they have other systems such as PHP configured.

You should be asking your hosting company what's changed on the server, if anything, and reporting to them that you're experiencing database disconnections (connections dropping) that you weren't seeing earlier.

They will want to know what *you* have changed, as well.


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
