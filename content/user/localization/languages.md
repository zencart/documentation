---
title: Language Packs 
description: Making Zen Cart multi-language 
category: localization
weight: 10
---

## What is a Language Pack ? 

A Language Pack is the group of files that contain the texts displayed on the pages of Zen Cart.  All the texts (constants) used in Zen Cart are in a fileset separated from the program files, to facilitate translation. The storefront and the admin have their own language fileset, each under a /languages directory.

By default, Zen Cart only includes the fileset for english (US). Other Language Packs are available from the Zen Cart [Plugins Library](https://www.zen-cart.com/downloads.php?do=cat&id=6) and from the Github repos of individual developers. 

Always read the corresponding support thread for a Language Pack to learn the current state of a language pack/how up to date it is and whether it is being maintained on a version control site like GitHub.

A Language Pack is a great deal of work to maintain and since they are all the results of efforts by the community, it is common that some languages are not kept up to date with the current Zen Cart.

Consequently, installing an older language pack in a current Zen Cart and having to update it yourself is something that you will need to accept if you want to use that language. It will not destroy your shop, but it will certainly result in multiple errors (white screens and corresponding debug logs) that are easily rectified. See the section below on Updating a Language Pack.

If updating is necessary, you should update the language pack BEFORE registering it in the Zen Cart admin.

## Installing a Language Pack

As always with any modifications, this should be tested and checked calmly and methodically in a **development copy** of your shop, **NOT** the production site, as older packs will take some time to be corrected/updated. 

If you're not familiar with installing a Zen Cart plugin, follow the instructions on 
[how to install a plugin](/user/plugins/how_to_install_a_plugin/). 

"Installing" has two steps.
1. Copying the files into the site. At this point the Zen Cart code will not try and use it and so no problems should occur.
If you know the pack needs updating, it should be done now, as described below.

2. Registering the new language in the Admin using 
[Admin > Localization > Languages > Add](/user/admin_pages/localization/languages/). 

Apart from adding the language option to the admin and the shopfront, the registering action will also create entries for the category and product names in the new language, by copying the english texts.
Since it is a good thing if this procedure executes without errors, it is advised to update the language pack first to hopefully avoid any errors. But, since this is being tested on a development site, it is not so critical.

## Updating a Language Pack

If the language pack is for an older version than the current Zen Cart, you should copy those files into a vanilla, current version of Zen Cart for comparison with the english fileset (using Beyond Compare/WinMerge or equivalent).

All files, the folder/file structure and the constant definitions that exist in the english files **must** be replicated/mirrored exactly in the additional language pack fileset. You may find that some texts may exist in the old pack but not in the new, but maybe they have been moved elsewhere. So, you should cut and save these "extra" constants to re-use when you discover where they were moved to.

If files or constants are missing in the language pack, at some point while navigating the shop the code will "look for" that definition and not find it, thereby causing a white screen but with a corresponding debug log that will tell you exactly what was not found. Hence easy to fix!

You should also consider the community aspect of Zen Cart and the free software you are using and ensure **your** valuable updating work is available to others, by locating a copy of the files on a public repository such as GitHub, to avoid others having to repeat your work and to allow others to improve it for everyone's benefit.

Here are some symptoms you might see.

### Blank White Screen After Language Pack Installed.

This is due to a missing file, syntax error in a file or a missing constant.

Check the logs directory for `myDEBUG-YYYYMMDD-HHMMSS-nnnnnn.log` files and look for `failed to open stream: No such file or directory`. Before it you should see a file path of the missing file. 
    
```
    PHP Warning: require_once(**YOURSITE/includes/languages/YOURLANGUAGE/MISSINGFILE.php**): failed to open stream: No such file or directory in YOURSITE/includes/languages/YOURLANGUAGE.php on line 607
``` 
    
Find the file in the english language folder `YOURSITE/includes/languages/english/MISSINGFILE.php` and copy to your language folder.

```
PHP Fatal error:  Uncaught Error: Undefined constant "MODULE_PAYMENT_MONEYORDER_TEXT_ACCOUNTS".... 
``` 
    
Find the constant name in the english language files and copy it to the corresponding file in the language pack. You can translate it now or later, or not at all if it is an admin file and you don't care. But it **MUST** exist.

**NOTE:** You must navigate through every page on the shop to check this as different files are loaded on different pages.

### Capitalized Titles Displayed in English

If you get sections named displayed as capitalized title with underscore between, e.g.`HEADING_TITLE`, again it will be because language files have not been included in the language pack. Finding these can be trickier as the same title may be used in multiple places. 

Start by logging into your admin page. Then select `Tools > Developers Tool Kit` in the tool kit and enter the name of the missing variable.  Search `All Language Files for ENGLISH - Catalog/Admin`. This should produce a list of places where the variable is defined.
 
- If it is only one place, then transfer that file from the english location to YOURLANGUAGE equivalent location.
- If there are multiple listings, then go back to the storefront and add `&language=en` to then end of the URL or if `&language=YOURLANGUAGECODE` is already present, change YOURLANGUAGECODE to `en`.  Then refresh the page and look at the correct wording. Use this wording to find the correct file and copy the file from the english location to YOURLANGUAGE equivalent location.

### Admin Field Descriptions Still in English

This means one of two things happened: 

- The language pack did not contain a full translation of the admin descriptions held in the database.  Contact the language pack creator to ask if translation is available.

OR

- You have not run the sql patch for the admin files.  See your installation instructions and run the sql patch.

### Some Texts Have Odd Characters Instead of Accented Letters

The language file that contains this text is not encoded in utf-8 with no BOM. You can open the file in a suitable editor (like Notepad++) to change the encoding, but if many files are not encoded correctly, there are free programs available that can encode all the files at once.

## Language Files from Zen Cart 1.5.8 onwards

The structure of the language files was completely changed in Zen Cart 1.5.8.

A description of the changes and conversion procedure is provided in the developer's guide to [158 Language Files](/dev/code/158_language_files/).

Developers wishing to work on language packs are referred to the [Creating a Language Pack](/dev/languages/creating_a_language_pack/) page.

