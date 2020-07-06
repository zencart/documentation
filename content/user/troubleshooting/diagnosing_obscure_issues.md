---
title: Diagnosing Obscure Issues
description: Diagnosing Obscure Issues in Zen Cart 
category: troubleshooting
weight: 10
---

## General Troubleshooting to find odd problems

The most detailed procedure to follow to find out what's wrong when you've made some system changes or just completed an upgrade but something's not working well, or you're getting unexplained results, would be:

1.  Download all your site's files with your [FTP tool](/user/first_steps/useful_tools/#ftp-tools) to a new temporary folder on your PC.
2.  Run a [file compare utility](/user/first_steps/useful_tools/#file-comparison-utility) to compare all your site's files against a freshly unzipped copy of the same version of Zen Cart. You can find [the original release ZIPs here.](http://sourceforge.net/projects/zencart/files/)
3.  Identify all the differences, and check each one to see if it could cause the problem.

**Things to look for are:**

*   Unexpected blank lines or spaces at top or bottom of files.
*   Customized code that's missing closing brackets ) or braces } or semicolons ; or quote marks ' and ".
*   Incomplete files that may have not been uploaded properly.
*   Plugins that have been installed, and whether they've been done right or not.
*   Files that have been upgraded incompletely.
*   Files that have been corrupted during upload by becoming double-spaced due to improper handling of end-of-line characters.

**Most Common Causes:**

*   In many cases it's a result of `define()` statements being customized and missing the closing `'` or `')` or `');` or maybe using `'` marks inside strings but not using `\'` instead so the `'` is treated properly.
*   Second most common root cause is poorly-written plugins.
*   Third most common is an incomplete upgrade of PHP files.

