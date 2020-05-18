---
title: Upgrading - Basic instructions 
description: Zen Cart Upgrading - Basic instructions 
category: Upgrading 
weight: 10
---

**READ THIS FIRST: [How do I rebuild my site on the new version, instead of upgrading?](https://www.zen-cart.com/entry.php?3-How-do-I-rebuild-my-site-on-the-new-version-instead-of-upgrading)**

Detailed upgrade instructions that help you retain your customizations while upgrading to new features, can be found in this [related article](/user/upgrading/detailed_upgrading/).

Before you begin, remember to make a [complete backup of your files and database](/user/running/backup/). 

Be sure to familiarize yourself with the content of the release (and any prior releases you are upgrading through to get to the new release).  You should review 

- Relevant **What's New** files in the [release directory](https://www.zen-cart.com/docs/). 
- The [Release Specific Considerations](/user/upgrading/release_specific_upgrade_considerations/) document. 

### <font color="#ff0000"> **A. If you want to PRESERVE YOUR CUSTOMIZATIONS, use these instructions [upgrading and preserving customizations](/user/upgrading/detailed_upgrading/)** </font>

### <font color="#333399">B. If you have NO CUSTOMIZATIONS (or don't wish to preserve the ones you have), here's a high-level overview/**summary** of a slightly shorter process:</font>

1.  Back up your site from the server as well as the copy on your computer.
2.  Backup your database
3.  Create a new directory and copy your site into it
4.  Then create a new database and load your old database in it
5.  Next, change the two configure.php files to utilize the new directory and database  This way ... when you attempt to upgrade you are "practicing" to see where the problems, if any will happen  
6.  Make sure all appears to be working on your temp site.
7.  Now load the "new" version files to your new temp directory from latest downloaded ZIP
8.  Run the http://www.YOURSITE.com/zc_install
9.  Choose the Upgrade Database option  
10.  Process each suggested step one at a time ... leave the first checkbox that the upgrader picked checked and uncheck the others.  
    -Advantage is that you can see your problems step by step  
    -Each time it completes it will recheck the boxes left to go.  
    -Continue in this method until all boxes are unchecked.
11.  If you find you have issues, you are not hurting anything and can always start over without damage to your existing shop and live database.  

### QUESTION: "Why is this process so long?"

**ANSWER:** Another way to look at it is this:  An "upgrade" is essentially a rebuilding of your site.  
The steps outlined above are the recommended way to do it so that you rebuild your site in a <u>temporary location,</u> letting you resolve all potential problems *before* you ever touch your actual live site. **This gives you time to sort out whatever needs sorting** "just in case", and allows you to keep taking sales while you're preparing the upgrade. It also helps take some of the pressure off and makes it less urgent to do it all in one fell swoop.  

The process of comparing your site against the original code for the old version is, in one sense, to simply help you quickly identify what customizations you need to make to put those same capabilities into your new site. It simply speeds the process and creates a sort of checklist of things for you to re-do on your new site.  

Then, after you've got it all built in the temporary location, you put your live store down for maintenance, quickly redo the upgrade there, and then bring it online ... meaning your actual live store's downtime could be as short as 5-10 minutes depending on complexities etc.  

So, follow the guide, and while there may be some learning involved and remembering of things you did awhile back, it's all time well spent.  

* * *

### QUESTION: "I have a very old version. Do I upgrade in stages, or all-at-once?"

**ANSWER:** You can upgrade to the latest version directly. When you do the database-upgrade step in zc_install it will show you all the database-version-levels which need upgrading, and will pre-check the checkboxes for you and will take care of upgrading through all those steps automatically. Usually you can just leave those boxes checked and put in the admin password and proceed with the upgrade, which normally will take just a few seconds.  
