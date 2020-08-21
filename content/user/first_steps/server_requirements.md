---
title: Server Requirements for running Zen Cart
description: What are the Server Requirements for running Zen Cart?
category: Installing
weight: 10
---
## Zen Cart specifications - Server Requirements

_(Last updated: July 23, 2020)_  

*Minimum* server requirements:  

*   Zen Cart operates on a standard "LAMP" stack: PHP, Apache, MySQL on most operating systems (Linux/macOS/Windows)
*   See the detailed version-compatibility details in the sections below.
*   Keep in mind that for security compliance, you should always use a PCI Compliant version of each of these required software components. That means using a ZC version that's compatible with those software component versions, too!

## SSL, OpenSSL, cURL

*   Zen Cart requires cURL to be installed/compiled into PHP with OpenSSL. If this capability is not available, a message to that effect will be displayed during the initial installation's system-inspection, however it will still allow installation anyway. It is up to you to ensure cURL is enabled. Consult your hosting company for assistance.
*   You should always use HTTPS (SSL) on your store. Yes, [you really do need an SSL certificate](/user/first_steps/yes_you_need_ssl/). Be sure to regularly test your site's SSL (https) using [www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/index.html) and have your hosting company resolve all reported issues. If your hosting company doesn't know how to resolve the issues to at least a "B" rating, find another hosting company.


## PHP Version

The following table shows the PHP versions compatible with each version of Zen Cart. 

**Note:** future versions of Zen Cart including v1.5.8 will require PHP 7.3+.

*   <font color="#ff0000">**Zen Cart v1.5.7** is designed for PHP 5.6 through PHP 7.4</font>
*   <font color="#ff0000">**Zen Cart v1.5.6** is designed for PHP 5.5 through PHP 7.3</font>
*   <font color="#ff0000">**Zen Cart v1.5.5** is designed for PHP 5.5 up to PHP 7.1</font> 
*   <font color="#ff0000">**Zen Cart v1.5.4** is designed for PHP 5.5 and PHP 5.6</font> 
*   **Zen Cart v1.5.3** is compatible with PHP 5.3.7 thru PHP 5.6 
*   **Zen Cart v1.5.2** is compatible with PHP 5.3.7 thru PHP 5.6 (or PHP 5.2.14 with weakened security)
*   **Zen Cart v1.5.1** is compatible with PHP 5.2.14 thru PHP 5.3.x.
*   **Zen Cart v1.5.0** is compatible with PHP 5.2.14 thru PHP 5.3.x.
*   **Zen Cart v1.3.9** series is compatible with PHP 5.2.10 thru PHP 5.3.x.
*   **Zen Cart v1.3.7-v1.3.8a** are compatible with PHP 4.3.2 thru PHP 5.2.x, but *not* PHP 5.3.
*   **Zen Cart v1.2.x through v1.3.6** are compatible with PHP 4.3.2 - 4.4.x. They are NOT compatible with PHP 5.

PHP compatibility requirements of Plugins may vary. Consult each plugin's documentation and support discussion-thread for details.  

<font color="#ff0000"> **Using the latest version of Zen Cart is always recommended for maximum compatibility.** </font>

### Which PHP version should I use?

It is best to **use the most recent PHP version that your Zen Cart version supports**. 

FYI: Consult [PHP's Version Support Policy](https://www.php.net/supported-versions.php) to understand whether your PHP version is still supported. Remember: old versions are not PCI compliant, and are not deemed "secure" if they are out of the maintenance period.

<font color="#ff0000">**NOTE:** PHP 5.x is officially obsolete. So are many of the early PHP 7 versions. You should be moving to the latest version of PHP (and matching Zen Cart version) as soon as possible!</font>  

### PHP Extensions/Modules used by Zen Cart

Zen Cart requires a few PHP modules/extensions installed: 

 - `curl`
 - `mysqli`, `pdo_mysql`
 - `zlib` - particularly beneficial to enable `zlib.output_compression`
 - `json`
 - `fileinfo`
 - `getimagesize()`
 - `gd`
 - `zip`

It is suggested to also enable the following PHP extensions:

 - `intl`, `mbstring`, `process`, `pdo_sqlite`

### PHP Memory Recommendations

- **memory_limit** suggested: **128M** or higher such as 256M or 512M if your server can handle it.
- **post_max_size** and **upload_max_filesize** should be set to whatever max file size you or your customers may upload. Usually **8M** is sufficient for most sites, but if you're accepting huge uploads, set both to the max size of accepted combined uploads.  

### PHP Settings for optimum security:

- ENABLE: `allow_url_fopen` is needed for checking things that don't/can't use `curl` (many shipping quote modules use this).
- DISABLE: `allow_url_include` should be OFF. Zen Cart never needs this.
- DISABLE FUNCTIONS: `passthru`, `system`, `shell_exec` are not used by Zen Cart (but might be used by some plugins).


## MySQL Version

The following table shows the MySQL versions compatible with each version of Zen Cart. 

**Note:** Future versions of Zen Cart including v1.5.8 will require MySQL 5.7.8+ or MariaDB 10.2.7+.

*   Zen Cart v1.5.7 expects MySQL 5.1 to 8.0, or MariaDB 10.1 to 10.4
*   Zen Cart v1.5.6 expects MySQL 5.1 to 5.7, or MariaDB 10.1 to 10.4 ("strict" errors may occur with 5.7 or 10.2)
*   Zen Cart v1.5.5 expects MySQL 5.1 to 5.7, or MariaDB 10.1 ("strict" errors may occur with 5.7 or 10.2)
*   Zen Cart v1.5.0 to v1.5.4 expects MySQL 5.1 to 5.5, and <u>may</u> work with MariaDB 10.1
*   Zen Cart v1.3.9 is compatible with MySQL 4.1.3+ thru 5.1
*   Zen Cart v1.2.x thru 1.3.8a were designed for MySQL 4, and will give errors on MySQL5

Plugin compatibility may vary.  

<font color="#ff0000"> **Using the latest version of Zen Cart is always recommended for maximum compatibility.** </font>

FYI: [MySQL's Version Support Policy](https://en.wikipedia.org/wiki/MySQL#Release_history)


## Apache

Zen Cart works primarily with Apache 2.4 or 2.2

### Apache modules

Recommended Apache modules include:** `expires`, `headers`, `env`, `alias`, `deflate`, `ssl`, `http2`, `mime`, `phpX`, `rewrite` (in addition to other standard/default modules).

## Nginx  
Zen Cart runs well on Nginx. But you must handle directory-security manually, as described here:

### Security
The default Zen Cart distribution contains numerous Apache .htaccess rules to aid in implementing security protections against malicious spoofing and other abuse. These will not give you any protections if you're running Nginx, so you will need to do those yourself.

At the end of initial installation some Nginx `conf` file content suggestions are provided which you could manually copy into your nginx master configuration, to provide those same protections.


## Windows Servers / IIS **NOT SUPPORTED** 
Zen Cart is not regularly tested or supported on Windows Servers or IIS.  We don't recommend IIS, and we don't provide any default-configuration scripts for IIS.


## Perl, Python, CGI and other languages?  
Zen Cart does not use Perl or Python or CGI.
