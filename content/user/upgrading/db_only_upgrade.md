---
title: Database-Only Upgrade Instructions
description: Quickie upgrading if you don't want to keep your customizations 
category: Upgrading
weight: 8 
---

<font size="12" color="red">Warning!</font>

This is not the [standard upgrade procedure](/user/upgrading/detailed_upgrading/).  It will DEFINITELY cause you to lose functionality associated with your older customizations and could break things as you will have configuration settings with no associated files (sideboxes, template, etc.).  

<hr>

Doing a database only upgrade might be appropriate in situations like this:

- you are coming from Zen Cart 1.5.4 or older version, and you don't have time or budget for a proper upgrade.  
- your hoster just [updated PHP to a version which is not compatible with your older Zen Cart software](/user/first_steps/server_requirements/#php-version).
- you have minimal customizations and your current template is not mobile compatible. 

You will lose your customizations, but you won't lose your data and you'll be using the latest software, which is more secure. 

You will be using the `responsive_classic` template initially.  You can always add a new template later after your store is up and running. 

### Setup 

1.  **CRITICAL:** [Back up your site](/user/running/backup/#step-1-backup-your-files) 
2.  **CRITICAL:** [Backup your database](/user/running/backup/#step-2-backup-your-database)
3.  Create a new directory called "test" and put the latest version of Zen Cart into it. We'll call this your *test site*. 
4.  Then create a new database and load your old database in it
5.  Do any database conversions necessary - only necessary if you have [custom
 date fields](/user/upgrading/date_standardization/)
6.  Next, change the two configure.php files to utilize the new directory and
database  This way ... when you attempt to upgrade you are "practicing" to see
where the problems, if any will happen
7.  Run the installer at `https://www.YOURSITE.com/zc_install`
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
1. Copy the `/images` folder from your live site onto your test site
2. Copy in any new images you created from your live site's `includes/templates/YOURTEMPLATE/images` folder to the test site's `includes/templates/responsive_classic/images` folder 
3. Copy in any new images you created from your live site's `email` folder to the test site's `email` folder 


### Customization
1. Customize the following files, referring to your live site to see what needs to be changed: 
- `includes/languages/responsive_classic/english.php`
- `includes/languages/english/responsive_classic/email_extras.php`
- `admin/includes/languages/english/email_extras.php`


### Testing 
1. Create a test order, take it all the way through to checkout success, then view the order in your test admin.  Make sure everything is working as expected.

### Updating PHP 

- [Update your PHP version](/user/upgrading/php_version/) if appropriate. 

## If you have a little more time ... 

It's worth your while to switch from the Responsive Classic template to the [Bootstrap template](/user/template/bootstrap/).  It looks much better and it's just a bit more work.  Redo the customization step above for the storefront files:
- `includes/languages/bootstrap/english.php`
- `includes/languages/english/bootstrap/email_extras.php`
