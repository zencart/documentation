---
title: What are the Server Requirements for running Zen Cart?
description: What are the Server Requirements for running Zen Cart?
category: Installing
weight: 10
---
## Zen Cart specifications - Server Requirements

_(Last updated: Dec 1, 2019)_  

*Minimum* server requirements:  

*   Zen Cart operates on a standard "LAMP" stack: PHP, Apache, MySQL on most operating systems (Linux/macOS/Windows)
*   See the detailed version-compatibility details in the sections below.
*   Keep in mind that for security compliance, you should always use a PCI Compliant version of each of these required software components. (That means using a ZC version that's compatible with those software component versions, too!)

## SSL, OpenSSL, cURL

*   Zen Cart requires cURL to be installed/compiled into PHP with OpenSSL. If this capability is not available, a message to that effect will be displayed during the initial installation's system-inspection, however it will still allow installation anyway. It is up to you to ensure cURL is enabled. Consult your hosting company for assistance.
*   **NOTE:** Use of HTTPS (ie: SSL) **is highly recommended** **for** the purpose of protecting the data you collect about your customers, and their payments. In fact, some payment modules require SSL in order to work, and using them without SSL is typically a violation of your TOS with your merchant bank and **PCI compliance**.
*   You should test your site's security using [www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/index.html) and have your hosting company resolve all reported issues.
*   It is STRONGLY RECOMMENDED that you ensure your server administrator knows how to configure the server's TLS capabilities to be compliant with latest security practices, else your payment processing may not work.

## PHP Version

**Using the latest version of Zen Cart is always recommended for maximum compatibility.**  

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

PHP compatibility requirements of Plugins/Addons may vary. Consult each plugin's documentation and support discussion-thread for details.  

**What about old PHP versions?** The life-cycle for PHP versions, according to the PHP developers, can be viewed at [http://php.net/supported-versions.php](http://php.net/supported-versions.php)  

<font color="#ff0000">**NOTE:** PHP 5.6 and older are officially obsolete and no longer supported, even for security patches. You should be moving to PHP 7 as soon as possible!</font>  

### PHP Modules used by Zen Cart

Zen Cart requires a few PHP modules enabled: cURL, MySQLi and Zlib.  
Optional modules: gd and mb_xxxxx. 

<u>**PHP Memory Recommendations**</u>  

- **memory_limit** suggested: **128M** 
- **post_max_size** and **upload_max_filesize** should be set to whatever max file size you or your customers may upload. Usually **8M** is sufficient for most sites, but if you're accepting huge uploads, set both to the max size of accepted combined uploads.  

## MySQL Version

*   Zen Cart v1.5.6 expects MySQL 5.1 to 5.7, or MariaDB 10.1 to 10.4
*   Zen Cart v1.5.5 expects MySQL 5.1 to 5.7, or MariaDB 10.1 (10.2 may trigger "strict" errors)
*   Zen Cart v1.5.0 to v1.5.4 expects MySQL 5.1 to 5.5 ... and <u>may</u> work with MariaDB 10.1
*   Zen Cart v1.3.9 is compatible with MySQL 4.1.3+ thru 5.1
*   Zen Cart v1.2.x thru 1.3.8a were designed for MySQL 4, and will give errors on MySQL5

Plugin/Addon-compatibility may vary.  

<font color="#ff0000"> ** Using the latest version of Zen Cart is always recommended for maximum compatibility. ** </font>


## Apache

*   Zen Cart works primarily with Apache 2.4 or 2.2
*   **Recommended Apache modules include:** expires, headers, env, alias, deflate, ssl, mime, phpX, rewrite (in addition to other standard/default modules).

## Nginx  
The default Zen Cart distribution contains numerous Apache .htaccess rules to aid in implementing security protections against malicious spoofing and other abuse.  

It also provides Nginx conf files at the end of installation which you could manually copy into your nginx master configuration, to provide those same protections.

## Windows IIS **NOT RECOMMENDED** 
Zen Cart is not regularly tested on IIS.  We don't recommend IIS, and we don't provide any default-configuration scripts for IIS.  

## Perl, Python, CGI and other languages?  
Zen Cart does not use Perl or Python or CGI.
