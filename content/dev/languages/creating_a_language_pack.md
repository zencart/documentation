---
title: Creating a New Translation
description: Creating a New Language Pack for Zen Cart 
weight: 100 
layout: docs
---
## Create folders and copy files

### Essential Files

To create a new language pack you should start by copying all the English files to your new language folder structure.

- Copy `includes/languages/english.php` to `includes/languages/YOURLANGUAGE.php`

- Copy `includes/languages/english/` and all sub directories to `includes/languages/YOURLANGUAGE/`

- Copy `admin/includes/languages/english.php` to `admin/includes/languages/YOURLANGUAGE.php`

- Copy `admin/includes/languages/english/` and all sub directories to `admin/includes/languages/YOURLANGUAGE/`

If old style image buttons are being used then you will also need to create

- `includes/templates/template_default/buttons/YOURLANGUAGE/` and

- `includes/templates/responsive_classic/buttons/YOURLANGUAGE/` then fill with images of the buttons in your language

### Prior to 1.5.7

Prior to version 1.5.7  the `emails` folder contained some English language sections in the templates. 

- `emails` modify the email template files contents from English to your language (these files will overwrite the original distribution files).

### Admin Extras

The Admin pages on zen cart hold a lot of information in the configuration table on the database. To do a complete conversion it will be necessary to convert the description fields to your chosen language. This will require a SQL patch.

### Locations of language files

These are the locations where you will find language files that may need translating.

- emails (Only required for v1.5.6 and earlier)

    - email_common.css

    - email_template_checkout.htm

    - more html files

- admin

    - includes

        - languages

            - english.php

            - english

               - admin_account.php


               - more php files

               - extra_definitions

                   - ckeditor.php

                   - more php files

               - images

                   - buttons

                       - button_add_profile.gif

                       - more gif files

               - modules

                   - newsletters

                       - newsletter.php 

                       - more php files

- includes

    - languages

        - english.php

        - english

           - account.php

           - more php files

           - classic

               - header.php

           - extra_definitions

               - cardinal3dsecure.php

               - more php files

               - classic

                   - empty.txt
               - responsive_classic

                   - product_free_shipping.php

           - html_includes

               - define_ask_a_question.php

               - more php files

               - classic

                   - define_checkout_success.php

                   - more php files

               - responsive_classic

                   - define_checkout_success.php

                   - more php files

           - images

               - icon.gif

           - modules

               - order_total

                   - ot_cod_fee.php

                   - more php files

                   - classic

                       - empty.txt

               - payment

                   - authorizenet.php

                   - more php files

                   - classic

                       - empty.txt

               - shipping

                   - flat.php

                   - more php files

                   - classic

                       - empty.txt

           - responsive_classic

               - icon_names.php

    - templates (**NOTE** The folders below are only needed if the store has turned OFF the CSS buttons feature.)

        - responsive_classic

            - buttons

                - english

                    - button_update_cart.png

        - template_default

            - buttons

                - english

                    - button_add_address.gif

                    - more gif files



**Note** You should have this complete directory structure with `english` replaced by `YOURLANGUAGE` so for welsh `YOURLANGUAGE` becomes `cymraeg`

## Modifying the Language Files

Having copied all the English files you should modify the define statements within the files to your chosen language.

e.g. for a Welsh language translation modifying english.php

``` 
// Define the name of your Gift Certificate as Gift Voucher, Gift Certificate, Zen Cart Dollars, etc. here for use through out the shop
  define('TEXT_GV_NAME','Tystysgrif Rhodd');
  define('TEXT_GV_NAMES''Tystysgrifau Rhodd');

// used for redeem code, redemption code, or redemption id
  define('TEXT_GV_REDEEM','Cod Adbrynu');

// text for gender
  define('MALE', 'Br.');
  define('FEMALE', 'Bns.');
```
**NOTE** Any files named `english.php` must be renamed to `YOURLANGUAGE.php`

Eg. For Welsh `english.php` becomes `cymraeg.php`

## Creating Overide File for Admin

- Get a full list of the descriptions used in admin.

  You can extract a full set of the admin descriptions from the configuration table. Using any database management tool.

  `SELECT configuration_key, configuration_title, configuration_description FROM configuration;`

  You will get a file containing:
  
```
STORE_COUNTRY, Country, The country my store is located in <br /><br /><strong>Note: Please remember to update the store zone.</strong>
STORE_NAME, Store Name, The name of my store
STORE_OWNER, Store Owner, The name of my store owner
STORE_ZONE, Zone, The zone my store is located in
...

```

- Create an override language defines file to override the descriptions on the database.

   - In `admin/includes/languages/YOURLANGUAGE/` create a file `configuration.php`

   - For each entry extracted from the database you need to create 2 define statements

       - One for the title, preceding the configuration key with `CFGTITLE_`:  
       `define('CFGTITLE_STORE_NAME', 'Store Name');`
       
       - One for the description, preceding the configuration key with `CFGDESC_`:  
       `define('CFGDESC_STORE_NAME', 'The name of my store');`
       
  E.g. To change the descriptions above from English to the Welsh your file could contain:  
```
<?php
/*
 * Admin configuration title and description overrides
 */
define('CFGTITLE_STORE_COUNTRY', 'Gwlad');
define('CFGDESC_STORE_COUNTRY', 'Y wlad y mae fy siop wedi\'i lleoli yn <br /> <br /> <strong> Nodyn: Cofiwch ddiweddaru\'r parth storfa. </strong>');
define('CFGTITLE_STORE_NAME', 'Enw\'r Storfa');
define('CFGDESC_STORE_NAME', 'Enw fy siop');
define('CFGTITLE_STORE_OWNER', 'Perchennog y Siop');
define('CFGDESC_STORE_OWNER', 'Enw perchennog fy siop');
define('CFGTITLE_STORE_ZONE', 'Parth');
define('CFGDESC_STORE_ZONE', 'Mae\'r parth y mae fy siop wedi\'i leoli ynddo');

...

```

It will be necessary to do this for every key you want to change.

## Add Your Language Icon

- Place an small image file into `includes\languages\images` to represent your language. This is often the flag of YOURLANGUAGE country.

## Making it User Friendly

- Include a file named _README.txt_ where you say something about what has been translated and what has not, along with any other information you feel is appropriate.

- Create installation instructions (_Install.txt_ or _Install.html_)

- Add the locale to your language files. We can guess it for them by editing the call to _setlocale()_ in the following files:

  `includes/languages/YOURLANGUAGE.php`

  `admin/includes/languages/YOURLANGUAGE.php`


```
// look in your $PATH_LOCALE/locale directory for available locales..
  $locales = ['en_US', 'en_US.utf8', 'en', 'English_United States.1252'];
  @setlocale(LC_TIME, $locales);
  define('DATE_FORMAT_LONG', '%A %d %B, %Y'); // this is used for strftime()
  define('DATE_FORMAT', 'm/d/Y'); // this is used for date()
```

## Making Language Pack Available to Others

Having completed your language pack please upload it to the [Language Packs](https://www.zen-cart.com/downloads.php?do=cat&id=6) section of the Plugins Library.

## Updating an Older Translation 
If a language pack is out of date, you can easily make it up to date by comparing the English language files from the Zen Cart version the language pack was made for against the English language files of the current Zen Cart version. 


Here's how to do that:
- [Download the Zen Cart version](https://sourceforge.net/projects/zencart/files/) that matches the original language pack and the Zen Cart version you wish to update the language pack for.
- Unpack the two packages into two separate directories.
- Open a comparison program like [Beyond Compare ](https://www.scootersoftware.com/download.php) or  [WinMerge](https://winmerge.org/downloads/) (for Windows only)
- Compare the two versions of the directories `includes/languages and admin/includes/languages`, and be sure to include subfolders.
- If a file exists only in the older release, delete it from your language pack.
- If a file exists only in the newer release, copy that English language file into your language pack and translate it.
- If a file has changed between the two versions, compare those English files to see what exact changes has been made, and update your language pack accordingly.
- if the store has turned **OFF** the CSS buttons feature
    - Compare the two versions of the directory `includes/templates/template_default/buttons/english/` and see if there are any new files. You may also consider updating the images if any have changed, but that's probably not strictly necessary.
    - Compare the two versions of the directory `includes/templates/responsive_classic/buttons/english/` and see if there are any new files. You may also consider updating the images if any have changed, but that's probably not strictly necessary.


**Please [share](https://www.zen-cart.com/downloads.php?do=cat&id=6) your updated translation with the community. Thank you!**
