---
title: Diagnosing Obscure Issues
description: Strategy for digging into root causes of problems
category: troubleshooting
weight: 10
---

## General Troubleshooting to find odd problems

The most detailed procedure to follow to find out what's wrong when you've made some system changes or just completed an upgrade but something's not working well, or you're getting unexplained results, would be:

1.  Download all your site's files with your [secure FTP tool](/user/first_steps/useful_tools/#ftp-tools) to a new temporary folder on your PC (after making sure you've checked your PC is free of viruses and any malware).
2.  Run a [file compare utility](/user/first_steps/useful_tools/#file-comparison-utility) to compare all your site's files against a freshly unzipped copy of the same version of Zen Cart. You can find the [original Zen Cart release ZIP files here](https://sourceforge.net/projects/zencart/files/).
3.  Identify all the differences, and check each one to see if it could cause the problem.

**Things to look for are:**

*   Unexpected blank lines or spaces at top or bottom of files.
*   Customized code that's missing closing brackets ) or braces } or semicolons ; or quote marks ' and ".
*   Incomplete files that may have not been uploaded properly.
*   Plugins that have been installed, and whether they've been done right or not.
*   Files that have been upgraded incompletely.
*   Files that have been corrupted during upload by becoming double-spaced due to improper handling of end-of-line characters.
*   Override files that have altered normal operation.
*   Recently-added widgets/snippets, especially JavaScript from 3rd party services.
*   Additional non-original files of any sort, especially those that contain "define" statements, since those can change normal operation.

**Most Common Causes:**

*   In many cases it's a result of `define()` statements being customized and missing the closing `'` or `')` or `');` or maybe using `'` marks inside strings but not using `\'` instead so the `'` is treated properly.
*   Second most common root cause is poorly-written plugins.
*   Next most common is an incomplete upgrade of PHP files.
*   Third-party JavaScript you've added to your site.
*   Configuration switch settings you've changed in your Admin

**Other Causes:**
*   While it's not the first thing to suspect, if someone has gained unauthorized access to your website's server and made changes to PHP or JS or CSS files, or altered contents of your database, then the side-effects of that are countless ... and might even be invisible until something "breaks" randomly. A deep inspection of all files and overrides plus all database table content is necessary in such cases.
