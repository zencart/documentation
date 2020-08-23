---
title: Technical - Converting from iso-8859-1 to utf8
description: Modern sites should use UTF8 or UTF8MB4
category: upgrading 
weight: 20
---

### Do I need to convert to UTF-8?

Since Zen Cart v1.5.0 all **new** sites install database tables with the UTF8 character-set.
If your site is from an older version, your database might still be in latin1 mode due to the server's master configuration. To change the database to utf8, use the instructions below.

## Converting to UTF8:

1\. Use this [conversion utility to convert your data to UTF8](https://www.zen-cart.com/downloads.php?do=file&id=1318) (AFTER MAKING AND TESTING A DATABASE BACKUP): [https://www.zen-cart.com/downloads.php?do=file&id=1318](https://www.zen-cart.com/downloads.php?do=file&id=1318)  
2\. (If you installed your site NEW since v1.5.0 or newer, then the following are ALREADY done for you. But, if you UPGRADED from a version prior to 1.5.0, then you will need to double-check each of the following:)  

1.  Edit <font color="#ff0000">/admin/includes/languages/english.php</font> (and all other <i>language_name</i>.php files in that folder) and set the define for CHARSET to 'utf-8'.  
    Do the same with the <font color="#ff0000">non-admin /includes/languages/english.php</font> (and other language_name.php files in that folder)  
    ... AND ...
2.  Also edit your <font color="#ff0000">two configure.php files</font> to set DB_CHARSET to 'utf8':  
    <font color="#8b4513">define('DB_CHARSET', 'utf8');  
    </font>(Remember, the configure.php files are most likely set to read-only on your server, so you'll need to change their permissions on the server to be writable before you can save the changes you're making.)  
    (Remember, you must do this for **both** your /YOURADMIN/includes/configure.php **and** /includes/configure.php )

## Ignoring UTF8 and using a different character set:

If you wish to stick with Latin1 (aka iso-8859-1) use the following steps. Note that there is no `latin1` support in Zen Cart since v1.5.5.

If your site IS RUNNING or you have UPGRADED FROM an older version of Zen Cart where your language files are/were set to iso-8859-1, and **if you don't have any specific need for extended-character multibyte support** (for example your store is only in english and only english-speaking customers visit your store), then you may find it best to keep your site in iso-8859-1 (aka "latin1") mode instead of converting to UTF8.  

To do this, you'll need to fix BOTH your admin and non-admin files:  

1.  Edit your upgraded english.php file to use the old CHARSET and setlocale settings (SEE YOUR OLD english.php FILE CONTENTS).  
    That is, in both the admin and non-admin configure.php files, KEEP the old references to iso-8859-1 INSTEAD of utf-8\. You can see these defines in your pre-upgrade english.php files.  
    Same with any other whatever_language.php files.  
    ... AND ...
2.  Also edit your two configure.php files to set DB_CHARSET to 'latin1' instead of 'utf8'  
    (add the line if it doesn't exist):  
    <font color="#8b4513">define('DB_CHARSET', 'latin1');</font>

<font color="#696969">Useful video about the history behind why UTF8 was created:</font> [https://www.youtube.com/watch?v=MijmeoH9LT4](https://www.youtube.com/watch?v=MijmeoH9LT4)
