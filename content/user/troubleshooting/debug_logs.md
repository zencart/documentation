---
title: Debug Logs 
description: Debug Logs in Zen Cart 
category: troubleshooting
weight: 10
---

### Utilities
The following tools are available to make log handling easier:

- [Display Log Files](https://www.zen-cart.com/downloads.php?do=file&id=1583) - View the contents of the log-files via an admin tool.
- [Log Manager](https://www.zen-cart.com/downloads.php?do=file&id=2123) - Automatically remove logs after a certain period of time.
- [myDEBUG log Backtrace](https://www.zen-cart.com/downloads.php?do=file&id=1879) - shows stack trace when a log is created. Built in to Zen Cart after 1.5.5. 
- [Report All Errors](https://www.zen-cart.com/downloads.php?do=file&id=1792) - shows more extensive error logging than is done by default in Zen Cart. 

### Reading a Log

A debug-log's contents can be a little cryptic, here's part of one created for ***zc156c***, showing the spacing when multiple logs occur on a single page-load:

```
[25-Mar-2020 17:19:28 Europe/Berlin] Request URI: /zc156c/index.php?main_page=index&cPath=63, IP address: ::1
#1  define() called at [C:\xampp\htdocs\zc156c\includes\languages\english\responsive_classic\index.php:35]
#2  require_once(C:\xampp\htdocs\zc156c\includes\languages\english\responsive_classic\index.php) called at [C:\xampp\htdocs\zc156c\includes\modules\require_languages.php:26]
#3  require(C:\xampp\htdocs\zc156c\includes\modules\require_languages.php) called at [C:\xampp\htdocs\zc156c\includes\modules\pages\index\header_php.php:44]
#4  require(C:\xampp\htdocs\zc156c\includes\modules\pages\index\header_php.php) called at [C:\xampp\htdocs\zc156c\index.php:36]
--> PHP Notice: Constant TABLE_HEADING_PRODUCTS already defined in C:\xampp\htdocs\zc156c\includes\languages\english\responsive_classic\index.php on line 35.

[25-Mar-2020 17:19:28 Europe/Berlin] Request URI: /zc156c/index.php?main_page=index&cPath=63, IP address: ::1
#1  define() called at [C:\xampp\htdocs\zc156c\includes\languages\english\responsive_classic\index.php:37]
#2  require_once(C:\xampp\htdocs\zc156c\includes\languages\english\responsive_classic\index.php) called at [C:\xampp\htdocs\zc156c\includes\modules\require_languages.php:26]
#3  require(C:\xampp\htdocs\zc156c\includes\modules\require_languages.php) called at [C:\xampp\htdocs\zc156c\includes\modules\pages\index\header_php.php:44]
#4  require(C:\xampp\htdocs\zc156c\includes\modules\pages\index\header_php.php) called at [C:\xampp\htdocs\zc156c\index.php:36]
--> PHP Notice: Constant TABLE_HEADING_QUANTITY already defined in C:\xampp\htdocs\zc156c\includes\languages\english\responsive_classic\index.php on line 37.
```

Note that I changed the `/includes/extra_configures/enable_error_logging.php` to enable ***all*** errors to be logged, that's why there are `PHP Notice` logs!

Each log-entry contains three (3) significant sections (not in this order):

1. A header
2. An identification of the _specific_ error.
3. A 'back-trace' of the PHP modules called when the issue occurred.

#### Log-entry: Header

Each log-entry *starts* with a line identifying the date and time, the URI and the IP address associated with the log's creation, e.g. `[25-Mar-2020 17:19:28 Europe/Berlin] Request URI: /zc156c/index.php?main_page=index&cPath=63, IP address: ::1`.

This information provides you with:

1. The date and time that the log was created, since your web-server's file-system time might be different from your store's time-zone!
2. The URI used to access the site when the issue arose, e.g. `http://example.com/zc156c/index.php?main_page=index&cPath=63`.  This gives you the link to use to replicate the issue.
3. The IP address being used to access the site.  

#### Log-entry: Specific Error

Each log-entry ends with a line identifying the specific issue being reported, e.g. `--> PHP Notice: Constant TABLE_HEADING_PRODUCTS already defined in C:\xampp\htdocs\zc156c\includes\languages\english\responsive_classic\index.php on line 35`.

This information provides you with:

1. The _severity_ of the issue, one of `PHP Notice`, `PHP Deprecated`, `PHP Warning` or `PHP Fatal error`.
2. A text-string describing the error, e.g. `Constant TABLE_HEADING_PRODUCTS already defined`.
3. An identification of the line number and PHP module name that was active when the issue was logged.

#### Log-entry: Back-Trace

The middle portion of each log-entry contains a back-trace (or [stack-trace](https://en.wikipedia.org/wiki/Stack_trace)) that identifies the sequence of PHP module 'calls' that lead to the issue, starting (`#1`) with the module for which the issue was logged and ending with the module name (e.g. `index.php`, for the example above) that started the page's output.  Each line-entry identifies a PHP statement (e.g. `define`) that was executed from a specific line-number of a specific PHP module.

Let's examine the back-trace provided by the first log-entry in the example given above.

| Calling Module:Line Number                                  | PHP Function |
| ----------------------------------------------------------- | ------------ |
| /index.php:36                                               | require      |
| /includes/modules/pages/index/header_php.php:44             | require      |
| /includes/modules/require_languages.php:26                  | require_once |
| /includes/languages/english/responsive_classic/index.php:35 | define       |

