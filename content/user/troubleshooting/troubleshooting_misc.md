---
title: Miscellaneous Troubleshooting Questions
description: Troubleshooting Zen Cart 
category: troubleshooting 
weight: -1 
---

{{< misc >}} 

--- 
### How do I read my configure.php files? 

See the article [configure.php files](/user/miscellaneous/configure/). 

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

    7.  Try the suggestions in this related FAQ article: [I can't stay logged in to my admin](/user/troubleshooting/cant_stay_logged_in_admin/)

3.  Apart from browser cache and cookies problems, the most common problem is not having the `https` correct in your `admin/includes/configure.php`  file.  
    See: [How do I enable SSL?](/user/installing/enable_ssl/)

4.  If your admin password has been forgotten, or if you've done an admin password reset but forgot what the new password was, you'll have to reset the password via the database. See the FAQ for [resetting the Admin password to default](/user/troubleshooting/reset_admin_password/). 
5.  If you've installed your site into a folder whose name contains spaces, rename the folder so that it doesn't have spaces anymore. Update your [configure.php files](/user/miscellaneous/configure/) accordingly.

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
### Parse error: unexpected T_STRING (or similar)

If you are getting an error similar to:

```
"Parse error: parse error, unexpected T_STRING in /var/www/myaccount/public_html/includes/languages/english/SOMETHING.php on line 28"
```

This typically means you have forgotten to put a `\` (backslash) before a `'` mark (single quote, apostrophe) in one of your `define()` statements in the language file reported.

Example:

```
define('TEXT_SOMETHING','This is something simple that\'s used as an example');
```

(notice the `\` in the word `that's`).

---
### Warning: Your Admin login is not secure 

If you are getting this message in your Admin area:

``
Warning: Your Admin login is not secure ... either you still have default login settings for: Admin admin or have not removed or changed: demo demoonly The login(s) should be changed as soon as possible for the Security of your Shop. For additional Security for the Admin please see the /docs
``

Go to [Admin > Admins > Admin Users](/user/admin_pages/admins/admin_users/)  You can then add/remove administrative accounts. To secure your site, you should remove the "demo" account (if there is one), or at least change its password.

You should also make sure your admin password is not "admin" (or some other easy to guess value).  To change a password, click on the *Reset Password* button.

We suggest using something at least 8 characters long, and including numbers, and not dictionary words.

---

### WARNING: An Error occurred, please refresh the page and try again.

This is a generic message which usually indicates your site is having problems accessing data in your MySQL database.

It could be a problem with:

- MySQL not running
- incorrect DB_xxxxxxx settings in either of your configure.php files
- syntax error in MySQL statements
- an incompatible addon, on an incorrectly-installed addon (such as SQL installation steps not completed properly)
- a hacker attempting to do something rogue or malicious with something on your site, and has been blocked because they've got syntax errors or are attempting to exploit a vulnerability that is NOT a problem on your site
- something wrong with the MySQL engine on your webserver, which your hosting company will likely need to resolve for you

To find out the actual REAL error message that's occurring, view your site's myDEBUG-xxxxxx.log files located in your site's `/logs` folder.  More information on accessing those logs is provided in [blank page troubleshooting](/user/troubleshooting/blank_page/). 

(For versions prior to 1.5, logs were stored in `/cache`.)

Once you've found the actual error message details from those logs, search for those messages using the search option on this page or in the main Zen Cart support forum for additional steps in resolving the problem.

Alternatively, to see the actual MySQL error message details, you can TEMPORARILY enable `STRICT_ERROR_REPORTING` as described in [the strict error reporting FAQ](/user/troubleshooting/strict_error_reporting/).

**NOTE:** This should ONLY be a TEMPORARY measure. FOR SECURITY REASONS, YOU MUST PUT IT BACK TO NORMAL WHEN DONE, since its use may give malicious visitors information they ought not to have about your site.

---

### Sorry! There seems to be a problem connecting to our database

If your database credentials have been altered incorrectly, you might receive an unexpected screen when visiting your store:

```
Sorry!
There seems to be a problem connecting to our database. Please give us a few minutes to remedy the problem. Thank you.
```

Common causes:

- You've changed your database name or database username on your webserver
- You've deleted the tables from the database on your server
- You've changed the `DB_PREFIX` setting in your [configure.php files](/user/miscellaneous/configure/) to a value that doesn't match the tables in your database
- You've edited your `/includes/configure.php` file and incorrectly altered the defined values for the various `DB_XXXXXX` settings contained therein. You should first go and fix those. Then make sure you've also got the correct values in the /your-renamed-admin-folder/includes/configure.php as well.

The error is specifically displayed when the `DB_XXXXXX` values (which mainly denote your database login credentials for MySQL) are used but return a security login error when trying to connect to the database.

If you don't know the correct database name, MySQL username and MySQL password, and database host name (servername),  then you need to talk to your hosting company's tech support staff for assistance.

**NOTE:** THIS ERROR MEANS THERE IS A PROBLEM ON *YOUR* SERVER. THE PROBLEM IS NOT WITH zen-cart.com AND ONLY YOU CAN FIX THE ERROR!

--- 

### My images are distorted/fuzzy/squished, help?

Your images are distorted because the images sizes are set to fixed dimensions, both height and width, and if your images are not the same ratio they will appear distorted.

To remedy this situation, go to [Admin > Configuration > Images](/user/admin_pages/configuration/configuration_images/).
On this page is a list of the various image sizes, choose the image size you wish to edit and set one of the dimensions to 0.

Make sure you also set the following two options:

- *Calculate Image Size* = true
- *Use Proportional Images on Products and Categories* =1.

This will allow your images to be resized according to their own proportions.

---

### Help! My admin password expired!
The PCI rules for password management require that admin users change their password every 90 days.

So, after 90 days has elapsed, the next time you log in to your Admin it will ask you to change your password. Simply follow the prompts to select a new password. Per PCI rules, you cannot re-use the last 4 passwords.

If you don't want to change it "now", you will not be allowed to complete login. But your current password will let you get back to the change-your-password screen again.

---

### How do I troubleshoot PHP Session Handling issues? 
See [the PHP SESSION handling FAQ](/user/troubleshooting/cant_stay_logged_in_admin). 

---
<!-- please keep this at the end --> 
{{< faq_questions >}}
