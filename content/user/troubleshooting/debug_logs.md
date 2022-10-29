---
title: Debug Logs 
description: How do I interpret a debug log? 
category: troubleshooting
weight: 10
---

Debug logs are created by Zen Cart when the PHP interpreter has an
error in creating a webpage.   These logs are a source of valuable information 
that can help you resolve the underlying cause of the problem. 

By default, log files are created in the `/logs` folder at the root of your store.  Some hosting setups handle this differently - see [missing log files](/user/troubleshooting/missing_log_files/) if you think this is happening to you.

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

### How to Fix Common Debug Logs
Many examples of debug logs and how to fix them are shown in [PHP Warnings and Deprecated messages after upgrading](/user/upgrading/php_warnings/). 

### Logs and Versioning
As PHP is improved and enhanced, things that didn't create a debug log in older PHP versions now do.  So if your hoster upgrades your PHP version, you might start seeing new logs.

Every version of Zen Cart that is released fixes a number of debug logs which occurred in prior releases, especially with PHP versions that were released after that version of Zen Cart was released.  
- You can see your Zen Cart and PHP versions on the Admin [Version](/user/first_steps/version/) screen. 
- You can see the mapping of [Zen Cart version to PHP version](/user/first_steps/server_requirements/#php-version) to compare your current PHP version and Zen Cart version. 
- You can see the [Release History of Zen Cart](/user/about_us/release_history/) to see how current your copy is.

So if you're seeing a lot of logs, and your Zen Cart version is old, and especially if it's not recent enough for your PHP version, you should [upgrade](/user/upgrading/). 

### Special Logs 
Some logs will follow special file naming conventions to make them more easily identifiable.   The following prefixes are used: 

- `myDEBUG-bounced-email-adm-` failure to send email from admin
- `myDEBUG-bounced-email-` failure to send email from storefront

### Utilities
The following tools are available for working with debug log files:

- [Log Manager](https://www.zen-cart.com/downloads.php?do=file&id=2123) - Automatically remove logs after a certain period of time.

These are for older versions of Zen Cart:

- [Display Log Files](https://www.zen-cart.com/downloads.php?do=file&id=1583) - View the contents of the log-files via an admin tool. Built in to Zen Cart since 1.5.7.
- [myDEBUG log Backtrace](https://www.zen-cart.com/downloads.php?do=file&id=1879) - shows stack trace when a log is created. Built in to Zen Cart since 1.5.5. 
- [Report All Errors](https://www.zen-cart.com/downloads.php?do=file&id=1792) - shows more extensive error logging than is done by default in Zen Cart. Built in to Zen Cart since 1.5.7.

