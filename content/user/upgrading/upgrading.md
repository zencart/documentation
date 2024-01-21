---
title: Upgrading - Quick Reference
description: Summary of Key Points For Upgrading
category: Upgrading 
weight: 1
---

## Key Points Related To Upgrading

- [Checking your available PHP versions](/user/upgrading/check_php_version)
- **[How To Upgrade - Detailed Guide](/user/upgrading/detailed_upgrading/) YES, READ THIS!!!!**
- [Why Upgrade?](/user/upgrading/about_upgrading/) (Protecting your site from bad actors)
- [Date Standardization](/user/upgrading/date_standardization/)
- [Release Specific Upgrade Considerations](/user/upgrading/release_specific_upgrade_considerations/)
- [Template Changes](/user/template/template_changes/)
- [Configuration Parameter Name Changes](/user/upgrading/configuration_name_changes/)

## Upgrading Approaches 
- [Standard Upgrade](/user/upgrading/detailed_upgrading/) - preserving your customizations
- [Database-Only Upgrade](/user/upgrading/db_only_upgrade/) - quickie upgrade if you want to start over; does not preserve customizations

## After Upgrading
- [Keep Your JavaScript Scripts Updated](/user/upgrading/javascript_updates/)
- [Should I Change My Database Character Set to UTF8?](/user/upgrading/convert_to_utf8/)
{{% post_upgrade_golive_links %}}

## Troubleshooting
- [Why Don't I See An Option To Upgrade My Database?](/user/upgrading/installer_no_upgrade/)
- [New PHP Warnings/Errors After Upgrading](/user/upgrading/php_warnings/)


## QUESTION: "But it seems like a long process ..."

**ANSWER:** It is!  An "upgrade" is essentially a rebuilding of your site.

The suggested upgrade process is the recommended way to do it so that you rebuild your site in a <u>temporary location,</u> letting you resolve all potential problems *before* you ever touch your actual live site. 

**This gives you time to sort out whatever needs sorting** "just in case", and allows you to keep taking sales while you're preparing the upgrade. 

It also helps take some of the pressure off and makes it less urgent to do it all in one fell swoop.  

The process of comparing your site against the original code for the old version is, in large part, to simply help you quickly identify what customizations you need to make to put those same capabilities into your new site. It simply speeds the process and creates a sort of checklist of things for you to do to re-build it all onto your new site.

Then, after you've got it all built in the temporary location, you put your live store [down for maintenance](/user/running/down_for_maintenance), quickly redo the upgrade there following your checklist and notes, and then bring it online ... meaning your actual live store's downtime could be as short as 5-10 minutes depending on complexities etc. 

So, follow the guide, and while there may be some learning involved and remembering of things you did awhile back, it's all time well spent.  



## QUESTION: "I have a very old version. Do I upgrade in stages, or all-at-once?"

**ANSWER:** You can upgrade to the latest version directly.<br>
For the "files" portion of the upgrade, simply use the latest version.<br>
And when you do the database-upgrade step via `zc_install` it will show you all the database-version-levels which need upgrading, and will pre-check the checkboxes for you and will take care of upgrading through all those steps automatically. Usually you can just leave those boxes checked and put in the admin password and proceed with the upgrade, which normally will take just a few seconds.  


## QUESTION: "I can't figure this out!  What do I do?" 

**ANSWER:** Upgrading is a complex and time consuming process that requires skills that many (if not most) shop owners just don't have.<br>
The good news is that Zen Cart has a [Commercial Help Wanted](https://www.zen-cart.com/forumdisplay.php?138-Commercial-Help-Wanted) forum, where you
can hire a contractor to do this work for you.

