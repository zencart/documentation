---
title: Regular Periodic Maintenance 
description: What you should do to keep your store running well 
category: Running
weight: 1
---

This is a partial list of regular maintenance activities you should do on your store.  You will want to to do these things between once a week and once a month, depending on how busy your store is. 

- Make a [database backup](/user/running/backup/).
- Handle [old admin activity logs](/user/admin_pages/admins/admin_activity_logs/) - archive them first, then purge them.
- Investigate any [debug logs](/user/troubleshooting/debug_logs/) which are present in your `/logs` folder.  If you are unfamiliar with handling debug logs, [read this first](/user/troubleshooting/blank_page/#working-with-debug-logs).
- Monitor the [Zen Cart Announcements](/user/about_us/announcements/) for security release notices. 
- Check to see if there is a [new Zen Cart version available](/user/admin_pages/admin_new_version_available/).  If there is, schedule your [upgrade](/user/upgrading/) to be sure you can get it done soon. It's also a good practice to keep track of [the PHP Version Support Policy](https://www.php.net/supported-versions.php) so you know when the [PHP version you are running](/user/admin_pages/admin_version/) is at or near end of life.
- Check your SSL certificate - they do expire and need to be renewed once a year.  If there's a glitch (like your credit card expiring), you will have the dreaded [broken padlock](/user/running/broken_padlock/) issue.
- Check your [JavaScript libraries](/user/upgrading/javascript_updates/). Be sure you're not running a version with known vulnerabilities. 
- Use [Google Chrome Inspect](/user/running/inspect/) or [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights) to test the performance of your site and look for problems.  Many other web page speed testing tools exist; try them too.
- Perform a [security audit](/user/security/security_recommendations/#12-things-to-check-up-on-regularly) on your site. 
- Check your [website accessibility](/user/accessibility/accessibility/). **This is particularly important for websites in the United States due to litigation risk.**
- Optional: Run "Optimize Database" from [Admin > Tools > Store Manager](/user/admin_pages/tools/store_manager/). 
- Be sure you are subscribed to the [Known Bugs](/user/about_us/known_bugs/) thread for your release.  Update your store as fixes are announced.

## Cleaning Up Disk Space

Periodically deleting from your website server all files that are no longer needed can go a long way to keeping your site running speedily and not triggering "out of disk space/quote" issues with your account.

It also makes your backups speedier and smaller, which helps both you and your customers and your hosting company.

Images and old backups are the biggest consumers of disk space.

Things to consider cleaning up:

- ancient files in the `/logs` folder (you can use the Display Logs tool in `Admin->Modules->Plugin Manager->Display Logs` to purge log files)
- temporary directories you've created for any reason, including temporary "backups" of old files or old directories as is often done when doing upgrades
- database backups that you might have generated, including but not limited to those in the `/admin/backups` directory (see NOTE below)
- old files in the `/images` directory and subdirectories such as for old products or wrong images you no longer use. These can take a lot of space.
- no-longer-needed artwork uploaded by customers (when they placed an order) in the `/images/uploads` directory (see NOTE below)
- ancient files in the `/cache` folder (see NOTE below)
- ancient files in the `/pub` folder (see NOTE below)
- no-longer needed files in the `/download` folder (see NOTE below)
- old templates you no longer use, especially their images and javascript files 
- admin activity logs -- should be exported via the Admin console and saved to your PC, and then the log reset via the Admin page. See the link in the section above.

> **NOTE:** Any of these directories that contain a ".htaccess" or "index.php" or "index.html" or "index.htm" file should keep those htaccess and index files because their purpose is usually to prevent unauthorized access to all the other files in those same directories. So, don't just delete the directory or everything in them. Keep these protective files as-is, and be sure to upgrade them between Zen Cart versions if changes have been made.

Also worth cleaning up, if you understand databases:

- email archive history, if enabled, can consume a lot of disk space. If you have it enabled but never use it, turn it off and empty/truncate the email_archive table
- payment module logs: if you're using a payment module which logs all its activity into the database you might explore exporting that table and truncate/emptying it

