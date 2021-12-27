---
title: Admin cron jobs 
description: Creating a cron job in your admin
category: code
weight: 10
---

[Cron](/user/first_steps/hosting/#cron) is a utility on Linux hosting accounts that allows you to automatically schedule jobs to run at specific intervals.  An example of a job you might want to run is the [exchange rate updater](/user/admin_pages/localization/currencies/#update-currencies). 

What if you want to create your own custom cron job? 

The easiest way to do this is simply to follow the example of the exchange rate updater.  The key points to note are as follows: 

- Copy the file `admin/currency_cron.php` to `admin/my-script_cron.php` Change the references to `currency_cron` to `my-script_cron`, and call your own function in place of `zen_update_currencies`. 
- Copy the file `admin/includes/auto_loaders/currency_cron.core.php` to `admin/includes/auto_loaders/my-script_cron.core.php`  Change the inclusion of `localization.php` to your own functions file.

Now you are ready to create a cron job in your hosting company's control panel to run the update automatically on a scheduled basis. The command to give it is as follows. Work with your hosting company's tech support team if you need help with determining the correct path and the correct php binary to call.

```
php /full/server/path/to/admin/my-script_cron.php
```

