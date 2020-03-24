---
title: Diagnosing Obscure Issues
description: Diagnosing Obscure Issues in Zen Cart 
category: running 
weight: 10
---

## General Troubleshooting to find odd problems

The most detailed procedure to follow to find out what's wrong when you've made some system changes or just completed an upgrade but something's not working well, or you're getting unexplained results, would be:

1.  Download all your site's files by FTP to a new temporary folder on your PC.
2.  Run [Beyond Compare](http://www.scootersoftware.com/download.php) or [WinMerge](http://winmerge.sf.net) or a similar Diff/comparison tool to compare all your site's files against a freshly unzipped copy of the same version of Zen Cart™. You can find [the original release ZIPs here.](http://sourceforge.net/projects/zencart/files/)
3.  Identify all the differences, and check each one to see if it could cause the problem.

**Things to look for are:**

*   Unexpected blank lines or spaces at top or bottom of files.
*   Customized code that's missing closing brackets ) or braces } or semicolons ; or quote marks ' and ".
*   Incomplete files that may have not been uploaded properly.
*   Mods that have been installed, and whether they've been done right or not.
*   Files that have been upgraded incompletely.
*   Files that have been corrupted during upload by becoming double-spaced due to improper handling of end-of-line characters.

**Most Common Causes:**

*   In most cases it's a result of define() statements being customized and missing the closing ' or ') or '); or maybe using ' marks inside strings but not using \' instead so the ' is treated properly.
*   Second most popular is poorly-written mods.
*   Third most common is an incomplete upgrade of PHP files.

**Handy Utility**

This handy utility can be used to find the cause of blank pages appearing unexpectedly: [http://www.zen-cart.com/forum/showthread.php?t=84613](http://www.zen-cart.com/forum/showthread.php?t=84613)

