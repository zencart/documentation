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


## Converting to UTF8MB4:

### 1\. Converting the database
Use this conversion utility to convert your data to UTF8 (AFTER MAKING AND TESTING A DATABASE BACKUP): 

[https://github.com/zencart/utf8mb4-converter](https://www.zen-cart.com/downloads.php?do=file&id=1318)

If you encounter errors converting certain tables due to bad data in them, simply fix the bad data and then re-run the script. While a full list of possible database-problems is beyond the scope of this article, common bad-data issues might include the following: 
- [bad date formats](/user/upgrading/date_standardization/) in existing data
- [broken tables](/user/upgrading/fixing_broken_tables/), such as broken auto-increments or corrupt indexes

### 2\. Configuring your store

You must also update your PHP files to indicate your UTF-8 intentions. 

  If you installed your site NEW since v1.5.0 or newer, then the following are ALREADY done for you.<br>
  But, if you UPGRADED from a version prior to 1.5.0, then you will need to double-check each of the following:

a. Check each of the following files to be sure that **if** a define for `CHARSET` is present that it is defined as **utf-8**. (If no define for `CHARSET` is present, skip that file and check the next one).

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
 
## Issues with Converting prior to 03/05/2021 

Versions of the converter `utf8mb4-conversion.php` and the older version, which was called `latin1-to-utf8-conversion.php`, prior to 03/05/2021 had an issue with incorrectly removing default values during the conversion.  A script exists to fix this issue; see the section "Missing Defaults" in the readme file for [https://github.com/zencart/utf8mb4-converter](https://github.com/zencart/utf8mb4-converter). 

Please note this issue only affects people who ran versions of this script prior to 03/05/2021. 

You will know you have this issue if database insert operations are failing because fields don't have default values.  For example, creating a new admin will fail with 

```
--> PHP Fatal error: 1364:Field 'prev_pass1' doesn't have a default value :: INSERT INTO admin
SET admin_name = 'admin',
admin_email = 'help@thatsoftwareguy.com',
admin_pass = '....',
admin_profile = 1,
pwd_last_change_date = now(),
```
You can also tell by schema inspection if you have this problem - instead of 

```
  prev_pass1 varchar(255) NOT NULL default '' 
```

you will see 

```
  prev_pass1 varchar(255) NOT NULL 
```

Similarly, creating a new customer account will fail with a message like 

```
--> PHP Fatal error: 1364:Field 'customers_referral' doesn't have a default value :: INSERT INTO zen_customers 
...
```
