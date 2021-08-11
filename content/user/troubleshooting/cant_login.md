---
title: I can't login to the Admin after installing Zen Cart
description: Post installation login issues 
category: troubleshooting
weight: 10
---

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

    7.  Try the suggestions in this related FAQ article: [I can't stay logged in](/user/troubleshooting/cant_stay_logged_in/)

3.  Apart from browser cache and cookies problems, the most common problem is not having the `https` correct in your `admin/includes/configure.php`  file.  
    See: [How do I enable SSL?](/user/installing/enable_ssl/)

4.  Try using another browser, turning off browser plugins or logging out of and then back in to your password manager.  Sometimes login failures are simply local environmental issues that you need to straighten out.

5.  If you've installed your site into a folder whose name contains spaces, rename the folder so that it doesn't have spaces anymore. Update your [configure.php files](/user/miscellaneous/configure/) accordingly.

If all else fails, you may need to reset your admin password via the database. See the FAQ for [resetting your admin password](/user/troubleshooting/reset_admin_password/). 
