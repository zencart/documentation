---
title: 'Warning: An Error occurred, please refresh the page and try again.'
description:  What do I do when this message is shown? 
category: troubleshooting
weight: 10
---


This is a generic message which usually indicates your site is having problems accessing data in your MySQL database.

It could be a problem with:

- MySQL not running
- incorrect DB_xxxxxxx settings in either of your configure.php files
- syntax error in MySQL statements
- an incompatible addon, on an incorrectly-installed addon (such as SQL installation steps not completed properly)
- a hacker attempting to do something rogue or malicious with something on your site, and has been blocked because they've got syntax errors or are attempting to exploit a vulnerability that is NOT a problem on your site
- something wrong with the MySQL engine on your webserver, which your hosting company will likely need to resolve for you

To find out the actual REAL error message that's occurring, view your site's myDEBUG-xxxxxx.log files located in your site's `/logs` folder.  More information on accessing those logs is provided in [blank page troubleshooting](/user/troubleshooting/blank_page/). 

Once you've found the actual error message details from those logs, search for those messages using the search option on this page or in the main Zen Cart support forum for additional steps in resolving the problem.

Alternatively, to see the actual MySQL error message details, you can TEMPORARILY enable `STRICT_ERROR_REPORTING` as described in [the strict error reporting FAQ](/user/troubleshooting/strict_error_reporting/).

**NOTE:** This should ONLY be a TEMPORARY measure. FOR SECURITY REASONS, YOU MUST PUT IT BACK TO NORMAL WHEN DONE, since its use may give malicious visitors information they ought not to have about your site.

