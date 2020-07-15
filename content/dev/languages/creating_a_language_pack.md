---
title: Creating a New Translation
description: Creating a New Translation Pack for Zen Cart 
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

- emails **NOTE** Only required for v1.5.6 and earlier

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

           - html_incldues

               - define_ask_a_question.php

               - more php files

               - classic

                   - define_checkout_success.php

                   - more php files

               - responsive_classic

                   - define_checkout_success.php

                   - more php files

           - images

               - en_CA.gif

               - more gif files

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

    - templates

        - responsive_classic

            - buttons

                - english

                    - button_update_cart.png

        - template_default

            - buttons

                - english

                    - button_add_address.gif

                    - more gif files



**Note** You should have this complete directory structure with `english` replaced by `YOURLANGUAGE`

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

## Creating SQL patch for Admin

You can extract a full set of the admin descriptions from the configuration table. Using any database management tool.

`SELECT configuration_key, configuration_description FROM configuration;`

You will get a file containing:
```
STORE_COUNTRY	The country my store is located in <br /><br /><strong>Note: Please remember to update the store zone.</strong>
STORE_NAME	The name of my store
STORE_OWNER	The name of my store owner
STORE_ZONE	The zone my store is located in
...

```

You then need to create a update file to modify the descriptions on the database.

E.g. To change the descriptions above from English to the Welsh you could use:

```
UPDATE configuration SET configuration_description = 'Y wlad y mae fy siop wedi'i lleoli yn <br /> <br /> <strong> Nodyn: Cofiwch ddiweddaru'r parth storfa. </strong>' WHERE configuration_key = 'STORE_COUNTRY';
UPDATE configuration SET configuration_description = 'Enw fy siop' WHERE configuration_key = 'STORE_NAME';
UPDATE configuration SET configuration_description = 'Enw perchennog fy siop' WHERE configuration_key = 'STORE_OWNER';
UPDATE configuration SET configuration_description = 'Mae\'r parth y mae fy siop wedi\'i leoli ynddo' WHERE configuration_key = 'STORE_ZONE';
...

```

it will be necessary to do this for every key you want to change.

## Making it User Friendly

- Include a file named _README.txt_ where you say something about what has been translated and what has not, along with any other information you feel is appropriate.

- Create installation instructions (_Install.txt_ or _Install.html_)

- Add the locale to your language files. We can guess it for them by editing the call to _setlocale()_ in the following files

includes/languages/<your language>.php

admin/includes/languages/<your language>.php


```
// look in your $PATH_LOCALE/locale directory for available locales..
  $locales = ['en_US', 'en_US.utf8', 'en', 'English_United States.1252'];
  @setlocale(LC_TIME, $locales);
  define('DATE_FORMAT_LONG', '%A %d %B, %Y'); // this is used for strftime()
  define('DATE_FORMAT', 'm/d/Y'); // this is used for date()

```
- Create an uninstall sql file to restore the English descriptions used by the admin pages.

## Making Language Pack Available to Others

Having completed your language pack please upload it to the [Zen Cart > Plugins > Language Packs ](https://www.zen-cart.com/downloads.php?do=cat&id=6) area.

## Updating an Older Translation 
If a language pack is out of date, you can easily make it up to date by comparing the English language files from the Zen Cart&trade; version that the language pack you wish to update was made for against the English language files of the new Zen Cart&trade; version you wish to update to.


Here's how to do that:
- [Download the Zen Cart&trade; version](https://sourceforge.net/projects/zencart/files/) that matches the original language pack and the Zen Cart&trade; version you wish to update the language pack for.
- Unpack the two packages into two separate directories.
- Open a comparison program like [Beyond Compare ](https://www.scootersoftware.com/download.php) or  [WinMerge](https://winmerge.org/downloads/) (for Windows&trade; only)
- Compare the two versions of the directories `includes/languages and admin/includes/languages`, and be sure to include subfolders.
-* If a file exists only in the older release, delete it from your language pack.
-* If a file exists only in the newer release, copy that English language file into your language pack and translate it.
-* If a file has changed between the two versions, compare those English files to see what exact changes has been made, and update your language pack accordingly.
- Compare the two versions of the directory `includes/templates/template_default/buttons/english/` and see if there are any new files. You may also consider updating the images if any have changed, but that's probably not strictly necessary.


**Please [share]((https://www.zen-cart.com/downloads.php?do=cat&id=6)) your updated translation with the community. Thank you!**
