---
title: Database-Only Upgrade Instructions
description: Lower cost quickie upgrading
category: Upgrading
weight: 8 
---

<font size="12" color="red">Warning!</font>

This is not the [standard upgrade procedure](/user/upgrading/detailed_upgrading/).  It will DEFINITELY cause you to lose functionality associated with your older customizations and could break things as you will have configuration settings with no associated files (sideboxes, template, etc.).  

<hr>

Doing a database only upgrade might be appropriate in situations like this:

- you are coming from Zen Cart 1.5.4 or older version, and you don't have time or budget for a proper upgrade.  
- your hoster just [updated PHP to a version which is not compatible with your older Zen Cart software](/user/first_steps/server_requirements/#php-version), and your cart no longer works.
- you have minimal customizations and your current template is not mobile compatible, and you just want to get current.

**You will lose your customizations**, but you won't lose your data and you'll be using the latest software, which is more secure. 

You will be using the `responsive_classic` template initially.  **You can always add a new template later after your store is up and running.**

### Setup 

Note that if you are building a test version of your cart that uses a different version of PHP than your live site, see [Multiple PHP Versions](/user/upgrading/multiple_php_versions/) for instructions, since the procedure is a little different. 

1.  **CRITICAL:** [Back up your site](/user/running/backup/#step-1-backup-your-files) 
2.  **CRITICAL:** [Backup your database](/user/running/backup/#step-2-backup-your-database)
3.  Create a new directory called "test" and put the latest version of Zen Cart into it. We'll call this your *test site*. 
4.  Then create a new database and load your old database in it
5.  Do any database conversions necessary - only necessary if you have [custom
 date fields](/user/upgrading/date_standardization/)
6.  Next, change the two configure.php files to utilize the new directory and
database  This way ... when you attempt to upgrade you are "practicing" to see
where the problems, if any will happen
7.  Run the installer at `https://www.YOURSITE.com/zc_install`.  **Note:** if your current PHP version is very old, you may need to change it to run the installer.  This will likely take down your live store.  If you aren't sure you can get this whole procedure done quickly, consider [setting up a test environment](/user/running/local_testing/) and doing the upgrade there. 
8.  Choose the *Upgrade* option

![Use the upgrade button!](/images/upgrade_button.png)

### The zc_install process 

Once you press the Upgrade button, the screen will show you a list of updates to be performed.

![Updates being performed](/images/full_db_upgrade.png)

**Be patient** - it can take a while to do all the updating required. 

Once this action completes, you have an up to date copy of your database.

### Database Changes

- Go to Admin > Tools > Template Selection and set your template to Responsive Classic (since your old template won't exist on your updated site).  
- Visit each of the admin pages Modules > Shipping, Modules > Payment, Modules > Order Total to allow your modules to insert any missing keys.   Some modules may require re-installation to add keys. 

### Copy from live site 
- Copy the `/images` folder from your live site onto your test site.
- Copy in any new images you created from your live site's `includes/templates/YOURTEMPLATE/images` folder to the test site's `includes/templates/responsive_classic/images` folder.
- Copy in any new images you created from your live site's `email` folder to the test site's `email` folder.


### Customization
- Customize only the critical language files. See [Basic 158+ Language Customizations](/user/localization/basic_158_language_customizations/).

### Testing 
- Create a test order, take it all the way through to checkout success, then view the order in your test admin.  Make sure everything is working as expected.

### Updating PHP 

- [Update your PHP version](/user/upgrading/php_version/).

## If you have a little more time ... 

It's worth your while to switch from the Responsive Classic template to the [Bootstrap template](/user/template/bootstrap/).  It looks much better and it's just a bit more work.  Redo the [basic language customizations](/user/localization/basic_158_language_customizations/) step for the storefront, using placing the files in `includes/languages/english/bootstrap`.

## After Golive 

{{% post_upgrade_golive_links %}}

