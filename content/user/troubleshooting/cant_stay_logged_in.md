---
title: Can't login or stay logged in or add-to-cart
description: PHP Session Handling in Zen Cart 
category: troubleshooting
weight: 10
---

This is likely a PHP Session Handling issue. 

Before you begin, be sure you are familiar with the structure and contents of [configure.php files](/user/miscellaneous/configure/). 

**THE FIRST THING TO TRY is this:**  

- Close all your browser windows  
- Open 1 browser window, and use it to clear your browser cache AND cookies.  
- If you browser has a Private Browsing mode, make sure you're NOT using "Private Browsing" mode, because that will prevent sessions/cookies from being usable  
- Reboot your computer  
- Turn off your firewall software and try again.  
- Ensure that your stylesheets don't contain any references to image files that don't exist on your server.  
- Test in a completely different browser. IE and Chrome are known to be problematic with cookies sometimes. Switching to FireFox is a good troubleshooting step.  

- Don't use spaces in your domain names, nor in the foldernames in which you've installed your store. If yours has a space in the path anywhere, you may have troubles. Rename the folder instead.  

**NEXT, try to rule out a bad SSL configuration:**  

- clear browser cache AND cookies and try again. If it's still not working:  
- temporarily edit your `/admin/includes/configure.php` and change `HTTP_SERVER` to a URL that does NOT start with `https` (just as a test)
- clear browser cache AND cookies and try again
- turn off any .htaccess URL rewrites you may have created (If you've created them wrong then the rewrites/redirects may be breaking everything).

**IS IT A DOMAIN NAME PROBLEM?**

- if your site is using just an IP address and not a named domain, then it's possible your sessions/cookies are getting confused.  Edit your 2 `configure.php` files and set your `HTTP_SERVER` to an actual domain name, NOT an IP address.  
- if you're using a domain name with `www` in it, try removing the `www` from it temporarily, again, in the `HTTP_SERVER` setting.  

**IF IT STILL WON'T WORK, read on:**  

- Admin login sessions (and customer login sessions) are managed via the PHP session-handling functionality.  
- When you log in, a session is generated. The session's name is `zenAdminId` for admin, or `zenid` for the store.  
- When a session is started, PHP attempts to set a cookie in your browser. That cookie is intended to store that session ID so that it doesn't need to be shown in the browser all the time (ie: with &zenid=243524524524525 etc) at the end of all your URLs.  
- If a cookie cannot be set, then PHP simply includes the session name and number (like above) on all your URLs in order to keep you logged in.  
- When you log out, or the session ID is lost, the session data is reset and your authentication data is removed, requiring login again.  

**Possible causes of session-mgmt problems include:**  

- SSL misconfiguration, or URL-rewrite/redirect misconfiguration
- cookies are blocked by firewall or by browser configuration  
- PHP is misconfigured or has certain session settings set to methods incompatible with Zen Cart such as session-auto-start and transitive-sid etc. The installer warns about these if they are a problem.  
- you have your site configured to store session data in files but your filesystem doesn't have permissions set in such a way as to allow storage of the data  
- you have your site set to store session data in the database but the database table ("sessions") is corrupt or database-storage is full and new records cannot be added.  

Is your "cache" folder set to writable (ie: chmod 755 or some other suitable value according to your server's configuration) ?  

**Other possibilities:**  

a) altered files on your server. In that case a proper checkup of all your files is in order: see [Diagnosing obscure issues](/user/troubleshooting/diagnosing_obscure_issues/). 

b) a server configuration change by the hosting company (such as a PHP version change or anything else that might result in changes to the master php.ini configuration for the server or your hosting account).  See [mapping of Zen Cart versions to PHP versions](/user/first_steps/server_requirements/#php-version) for more information about which PHP versions are compatible with your Zen Cart version.

c) domain/SSL changes made to your DNS or hosting account.


