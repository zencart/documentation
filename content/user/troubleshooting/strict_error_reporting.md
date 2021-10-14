---
title: What is STRICT_ERROR_REPORTING
description: How do I use this setting? 
category: troubleshooting
weight: 10
---

`STRICT_ERROR_REPORTING` is a setting that can be used by developers to tell the store to override its normal security protection mode, which prevents the display of error messages to your screen.

Caveat: Outputting errors to the screen can cause some screens or features to not work correctly, especially those which involve being forwarded to another page based on certain criteria or after certain steps are completed.

Caveat: Also, using this option poses a security risk because error messages will disclose path and database information to malicious visitors who attempt rogue behaviors on your store. THUS, THIS SETTING SHOULD ONLY BE USED IN AN OFFLINE DEVELOPMENT ENVIRONMENT. Using it on a live store poses risks, and should only be used for short-term troubleshooting of a problem which can't be solved any other way.

### Enabling STRICT_ERROR_REPORTING
To enable `STRICT_ERROR_REPORTING`, simply use your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to upload a simple file to your store's site like this:

- For storefront problems, put it at: `/includes/local/configure.php`
- For admin problems, put it at: `/admin/includes/local/configure.php`

```
<?php define('STRICT_ERROR_REPORTING', TRUE);
```

### Disabling STRICT_ERROR_REPORTING
When you're done, simply delete the file you just created above. 

If that doesn't disable it, then that means you've enabled it in another file on your server. You will need to search your entire site for that define statement and remove it. (See the [Developer's Toolkit](/user/admin_pages/tools/developers_tool_kit/) for that.)

### Is this the same as STRICT mode?
No - STRICT mode is a database setting. They are not related.  [Read about STRICT mode](/user/troubleshooting/db_strict_mode/).

