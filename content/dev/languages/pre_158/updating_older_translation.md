---
title: Updating an Older Translation (DEPRECATED - 1.5.7 and below)
description: How to Update an Older Translation Pack to the Latest Version of Zen Cart
weight: 100 
layout: docs
---
If a language pack is out of date, you can easily bring it up to date by comparing the English language files from the Zen Cart version the language pack was made for (or last updated for) against the English language files of the current Zen Cart version. 


# Here's How to do That:

- [Download the Zen Cart version](https://sourceforge.net/projects/zencart/files/) that matches the original language pack and the Zen Cart version you wish to update the language pack for.

- Unpack the two packages into two separate directories.

- Open a comparison program like [Beyond Compare](https://www.scootersoftware.com/download.php) or [WinMerge](https://winmerge.org/downloads/)

- Compare the two versions of the directories `includes/languages and admin/includes/languages`, and be sure to include subfolders.

- If a file exists only in the older release, delete it from your language pack. (TIP: You might do the deletes last in case some of the things in these files have been relocated to other files ... in which case you might want to move those already-translated defines to the new location to save yourself some translating work)

- If a file exists only in the newer release, copy that English language file into your language pack and translate it.

- If a file has changed between the two versions, compare those English files to see what exact changes has been made, and update your language pack accordingly. This includes adding new defines and translating them, as well as identifying what got changed in existing English text that requires updating the prior translation of that define.

- to support older stores which have turned **OFF** the CSS buttons feature (or are so old that they don't have the choice), you could update the button images:

    - Compare the two versions of the directory `includes/templates/template_default/buttons/english/` and see if there are any new files. You may also consider updating the images if any have changed, but that's probably not strictly necessary.
    
    - Compare the two versions of the directory `includes/templates/responsive_classic/buttons/english/` and see if there are any new files. You may also consider updating the images if any have changed, but that's probably not strictly necessary.


**Please [share your updated translation with the community](https://www.zen-cart.com/downloads.php?do=cat&id=6). Thank you!**
