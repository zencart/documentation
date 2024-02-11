---
title: Converting from iso-8859-1 to utf8 or utf8mb4
description: Modern sites should use UTF8 or UTF8MB4
category: upgrading 
weight: 10
---

{{< technical >}}

## Do I need to convert to UTF-8?

**Short answer: yes.**

Modern databases can handle "multibyte characters" such as emojis. Older databases cannot.

If your customers enter emoji symbols in order-comments or contact-us emails, it may trigger errors on your store resulting in unexpected results and lost details. Sometimes spammers use these symbols in an effort to trip up your store with error logs and wasted CPU processing.

Also, older database structures don't handle non-english characters as well as utf8 does, [which is why utf8](https://www.youtube.com/watch?v=MijmeoH9LT4) has been the international "standard" for many years.

### What does my store currently use?
Since Zen Cart v1.5.0 all **new** sites create database tables with the UTF8 character-set.<br>
Since Zen Cart v1.5.6 all **new** sites create database tables with the UTF8MB4 character-set.

If your site was created from an older version, your database might still contain older database structures that don't support modern multibyte characters.

**To change the database to utf8mb4, use the instructions below.**

## Who cares about modern multibyte characters? 
You do!  

- Your customer might use an emoji in the comments field: 
```
Please deliver as fast as possible! 😄
```
- Your customer might have an accent or other special character in their name or address.   
```
Katrín Tanja Davíðsdóttir
```

In some cases, data entry like this can cause corruption (or worse, a white screen) if you're not using utf8mb4.

**To change the database to utf8mb4, use the instructions below.**

## Pre-Conversion to UTF8

If your database contains a mix of latin1 and utf8, it is sometimes helpful to pre-convert your database to entirely utf8 before attempting the move to utf8mb4. 
Use the plugin [Convert Zen Cart Database Conversion Tool](https://www.zen-cart.com/downloads.php?do=file&id=2367) to do this.

## Converting to UTF8MB4:

### 1. Converting the database
Use this plugin to convert your data to UTF8 (AFTER MAKING AND TESTING A DATABASE BACKUP): 

[Convert Zen Cart Database Conversion Tool](https://www.zen-cart.com/downloads.php?do=file&id=2367)

If you encounter errors converting certain tables due to bad data in them, simply fix the bad data and then re-run the script. While a full list of possible database-problems is beyond the scope of this article, common bad-data issues might include the following: 
- [bad date formats](/user/upgrading/date_standardization/) in existing data
- [broken tables](/user/upgrading/fixing_broken_tables/), such as broken auto-increments or corrupt indexes

The converter gives nicely formatted error output that allows you to isolate any issues. 

![Database Conversion issue](/images/convert_db.png)


### 2. Configuring your store

You must also update your PHP files to indicate your UTF-8 intentions. 

  If you installed your site NEW since v1.5.0 or newer, then the following are ALREADY done for you.<br>
  But, if you UPGRADED from a version prior to 1.5.0, then you will need to double-check each of the following:

a. Check each of the following files to be sure that **if** a define for `CHARSET` is present that it is defined as **utf-8**. (If no define for `CHARSET` is present, skip that file and check the next one).

For Zen Cart 1.5.8 and above: 
  - `/admin/includes/languages/lang.english.php`
  - `/admin/includes/languages/lang.OTHER_LANGUAGE_NAME.php` (if any)
  - `/includes/languages/lang.english.php`
  - `/includes/languages/TEMPLATE_NAME/lang.english.php` (if any)
  - `/includes/languages/lang.OTHER_LANGUAGE_NAME.php` (if any)
  - `/includes/languages/TEMPLATE_NAME/lang.OTHER_LANGUAGE_NAME.php` (if any)

For older versions of Zen Cart: 
  - `/admin/includes/languages/english.php`
  - `/admin/includes/languages/OTHER_LANGUAGE_NAME.php` (if any)
  - `/includes/languages/english.php`
  - `/includes/languages/TEMPLATE_NAME/english.php` (if any)
  - `/includes/languages/OTHER_LANGUAGE_NAME.php` (if any)
  - `/includes/languages/TEMPLATE_NAME/OTHER_LANGUAGE_NAME.php` (if any)
    
b. Check your `configure.php` files:
  - `/admin/includes/configure.php`
  - `/includes/configure.php`
  
  If they have a define for `DB_CHARSET`, make sure it is set to **utf8** without the dash (not `utf-8`). (It may not be present: if so, that's fine, go to the next file.)
  
  (Remember, the `configure.php` files are most likely set to read-only on your server, so you'll need to change their permissions on the server to be writable before you can save the changes you're making.)  
 
## Prior versions of the database converter 

Older versions of the convert such as `utf8mb4-conversion.php` and 
`latin1-to-utf8-conversion.php` are deprecated and no longer recommended. 

[Some notes on older versions of the database converter](/user/upgrading/old_converter/) are maintained for those who used it in the past. 
