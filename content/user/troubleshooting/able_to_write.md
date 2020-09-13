---
title: 'Warning: I am able to write to the configuration file' 
description: How do I make configuration files read-only? 
category: troubleshooting 
weight: 10
---

This error is triggered because the permissions on the file are set to Read,Write and Execute (UNIX) or on Windows no attributes are checked in the file properties.

On Linux/UNIX: Open the `/includes/` directory and, using CHMOD, set the permissions to 444. (Some systems may prefer 644)

On Windows: Open the `/includes/` directory, right click on the `configure.php` file and check the "Read Only" status.

Sometimes you have to do this via a File Manager tool provided by your webhosting provider. In cPanel, it's called File Manager. In other tools it might be called something different. In the file manager, you can simply navigate to the file you want to alter permissions for, then click on the File Properties link/button and set permissions. The links could have varying names.

If your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) won't let you set CHMOD 444 and 644 doesn't work successfully, you'll have to use the File Manager approach above. If that doesn't work, then you must contact your hosting company's tech support to ask them to do it for you.  Sometimes, although rare, it's necessary to set these files to 400 instead of the common 444 or 644.  Any lower than 400 may cause you to lose access to the file.

Some hosts have security configured such that even when you "ask" the server to set the files to 444, they remain at 644 or even get changed again later by a server security or filesystem properties check.  This is why on our support forum you'll find folks asking you to check and double-check what the permissions "really" are set to.

If you don't address this issue, then you leave your site vulnerable to security risks.  The warning is telling you that if someone were to get past Zen Cart's security systems, or if they were to hack into your server using some other less-secure program even on somebody else's hosting account, they could possibly read or change those very important configuration files.  Thus it's important to find a way to prevent the warning message, rather than merely suppress it.

The message is saying that the webserver, using PHP, *is* able to write to the file, according to the access check that PHP does against the file.  Zen Cart is simply reporting that there's a risk.  Please don't ignore or bypass it.  It's for your own security.

For assistance on changing permissions settings, see [How Do I Set Permissions on Files/Folders](/user/installing/permissions/).

Reference: Guide on [understanding what these CHMOD numbers mean](/user/installing/chmod/).

