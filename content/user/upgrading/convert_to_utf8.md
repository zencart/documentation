---
title: Technical - Converting from iso-8859-1 to utf8
description: Modern sites should use UTF8 or UTF8MB4
category: upgrading 
weight: 20
---

### Do I need to convert to UTF-8?

Modern databases can handle "multibyte characters" such as emojis. Older databases cannot.
If your customers enter emoji symbols in order-comments or contact-us emails, it may trigger errors on your store resulting in unexpected results and lost details.
Also, older database structures don't handle non-english characters as well as utf8 does, which is why utf8 has been the international "standard" for many years.

Since Zen Cart v1.5.0 all **new** sites install database tables with the UTF8 character-set.
Since Zen Cart v1.5.6 all **new** sites install database tables with the UTF8MB4 character-set.

If your site is from an older version, your database might still contain older data structures that don't support modern multibyte characters.

To change the database to utf8mb4, use the instructions below.

## Converting to UTF8MB4:

1\. Use this [conversion utility to convert your data to UTF8](https://github.com/zencart/utf8mb4-converter) (AFTER MAKING AND TESTING A DATABASE BACKUP): [https://github.com/zencart/utf8mb4-converter](https://github.com/zencart/utf8mb4-converter)  

2\. Update your PHP files to indicate your UTF-8 intentions. (If you installed your site NEW since v1.5.0 or newer, then the following are ALREADY done for you. But, if you UPGRADED from a version prior to 1.5.0, then you will need to double-check each of the following:)  

a.  Edit <font color="#ff0000">/admin/includes/languages/english.php</font> (and all other <i>language_name</i>.php files in that folder) and set the define for CHARSET to 'utf-8'.  
    Do the same with the <font color="#ff0000">non-admin /includes/languages/english.php</font> (and other language_name.php files in that folder)  
    ... AND ...
b.  Also edit your <font color="#ff0000">two configure.php files</font> to set DB_CHARSET to 'utf8':  
    <font color="#8b4513">define('DB_CHARSET', 'utf8');  
    </font>(Remember, the configure.php files are most likely set to read-only on your server, so you'll need to change their permissions on the server to be writable before you can save the changes you're making.)  
    (Remember, you must do this for **both** your /YOURADMIN/includes/configure.php **and** /includes/configure.php )


ASIDE: <font color="#696969">Useful video about the history behind why UTF8 was created:</font> [https://www.youtube.com/watch?v=MijmeoH9LT4](https://www.youtube.com/watch?v=MijmeoH9LT4)
