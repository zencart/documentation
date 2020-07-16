---
title: Language Support 
description: Making Zen Cart multi-language 
category: localization
weight: 10
---

### What is a Language Pack ? 

In Zen Cart, the messages displayed by the storefront and admin area
are kept in a separate area so they can be converted from English to any 
other language. 

Languages for your cart may be managed in 
[Admin > Localization > Languages](/user/admin_pages/localization/languages/). 

## Installing a Language Pack

To make your store multi-lingual, add the language in your admin using 
[Admin > Localization > Languages > Add](/user/admin_pages/localization/languages/). 

Once you have added a new language, you will need to get the language pack files that 
correspond to that language.  Language packs may be found in 
the [Plugins Library](https://www.zen-cart.com/downloads.php?do=cat&id=6).

Language packs are structured to correspond to your cart folders, so you can just 
rename the admin folder, if one exists, and then upload all the files. 

If you're not familiar with installing a Zen Cart plugin, follow the instructions on 
[how to install a plugin](/user/plugins/how_to_install_a_plugin/). 

## Troubleshooting a Language Pack
Here are some symptoms you might see, and ideas on how to resolve them.

### Blank White Screen (on Storefront) After Language Pack Installed.

There are likely to be missing language files. Check the logs directory for `myDEBUG-YYYYMMDD-HHMMSS-nnnnnn.log` files and look for `failed to open stream: No such file or directory`. Before it you should see a file path of the missing file. 
    
```
    PHP Warning: require_once(**YOURSITE/includes/languages/YOURLANGUAGE/MISSINGFILE.php**): failed to open stream: No such file or directory in YOURSITE/includes/languages/YOURLANGUAGE.php on line 607
``` 
    
Find the file in the english language folder `YOURSITE/includes/languages/english/MISSINGFILE.php` and copy to your language folder.
    
**NOTE:** You may have to repeat this task multiple times for older version language packs.

### Capitalised Titles Displayed in English

If you get sections named displayed as capitalised title with underscore between, e.g.`HEADING_TITLE`, again it will be because language files have not been included in the original language pack. Finding these can be more tricky as the same title may be used in multiple places. 

Start by logging into your admin page. Then select `Tools > Developers Tool Kit` in the tool kit, and enter the name of the missing variable.  Search `All Language Files for ENGLISH - Catalog/Admin`. This should produce a list of places where the variable is defined.
 
- If it is only one place, then transfer that file from the english location to YOURLANGUAGE equivalent location.
- If there are multiple listings, then go back to the storefront and add `&language=en` to then end of the URL or if `&language=YOURLANGUAGECODE` is already present, change YOURLANGUAGECODE to `en`.  Then refresh the page and look at the correct wording. Use this wording to find the correct file and copy the file from the english location to YOURLANGUAGE equivalent location.

### Admin Field Descriptions Still in English

- The language pack did not contain a full translation of the admin descriptions held in the database.  Contact the language pack creator to ask if translation is available.

OR

- You have not run the sql patch for the admin files.  See your installation instruction and run the sql patch.

