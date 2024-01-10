---
title: Server/Version Info 
category: admin_pages
weight: 10
---

Clicking [Version](/user/admin_pages/admin_version/) on the top right Admin navigation menu gets you to this page.  &nbsp;&nbsp;&nbsp; ![Version Link](/images/skinny_version.png)

The Server/Version info page allows you to view information about the server 
on which you are running Zen Cart. 

The information at the top of the page gives you a quick snapshot of the most 
critical server configuration items: 

- (a) PHP Version: Version of PHP you are using
- (b) Database Engine: Version of MySQL you are using
- (c) PHP Memory Limit: The amount of memory a script is allowed to allocate, per the [PHP Documentation on this setting](https://www.php.net/manual/en/ini.core.php#ini.memory-limit).  Read more about choosing an initial value for memory limit in [PHP memory limit and Zen Cart](/user/first_steps/server_requirements/#php-memory-recommendations), and checking and updating the value in [PHP memory_limit](/user/running/memory_limit/)
- (d) Database: (Since Zen Cart 1.5.6) the name of the database from your `admin/includes/configure.php` file 

Next is information about Zen Cart itself: 
- (e) history of your database
- (f) your Zen Cart version

Note: The best practice is to be running the [latest Zen Cart version](/user/first_steps/get_zen_cart/). 

Next, below (a) is the output of [`phpinfo()`](https://www.php.net/manual/en/function.phpinfo.php). 

<img src="/images/version_info_zc_156.png" alt="Zen Cart Version information" />
<br>

Be sure the version of PHP (a) you are running is a 
[supported version](https://www.php.net/supported-versions.php). 
Running an older unsupported version leaves you vulnerable to attack 
by bad guys.  Note that updating PHP sometimes means [upgrading your Zen Cart software](/user/upgrading) so that you're running the [latest Zen Cart version](/user/first_steps/get_zen_cart/). 

If your Database Engine (b) value shows *MariaDB*, 
then, if needed, you can see the 
[MySQL to MariaDB compatibility matrix here](https://mariadb.com/kb/en/mariadb-vs-mysql-compatibility/).

If you are coming to this page because of a new problem with your cart, be sure your Zen Cart version (f) is compatible with your PHP version (a).  Refer to the [PHP Version - Zen Cart version compatibility matrix](/user/first_steps/server_requirements/#php-version). 

## More Info on Version Checking

-  You may [disable Zen Cart version checking](/user/speed/admin_slow/) if you are having problems with it.  
- Some plugins have their own [plugin version checking](/dev/plugins/tips/#automatic-new-version-checks), which sometimes causes issues.  You may [disable plugin version checking](/user/plugins/version_check/). 


