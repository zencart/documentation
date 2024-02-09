---
title: Multiple PHP Versions
description: Running more than one version of PHP 
category: upgrading 
weight: 10
---

If you want to run multiple versions of PHP on your server (for example, to keep a live site going with an older version and test an upgrade with a newer version), these instructions should help.

If you are unfamiliar with the terms webroot, YOURACCOUNT and YOURSITE, please see [basic terms](/user/first_steps/basic_terms/).

First, you should verify that the desired [PHP Version is available](/user/upgrading/php_version/) on your host.

Generally your host will only allow you to run one version of PHP per domain.  But if you create one or more subdomains, each subdomain may also have its own version of PHP.  

## Create an alternate webroot 
With cPanel’s File Manager, navigate to `/home/YOURACCOUNT/`. This is known as "above webroot." If your cPanel File Manager loads with `/public_html`, just click on "Up One Level" to be “above the root.”  This is where you will place your test site.  Create a folder called "test" to hold the contents of your test site.

## Creating a Subdomain.
In cPanel, navigate to the Domains Section and click on the Create a New Domain option. 

![Subdomain](/images/sub_domain_1.png)

We now need to create the subdomain `test`.

In the Domain block, make sure the domain is showing `test.YOURSITE.com`.

Make sure the Share document root is not checked, and that the folder we just created is specified in the text field below.  Click Submit. 

![Subdomain 2](/images/sub_domain_2.png)

You now have a subdomain of `test.YOURSITE.com` ready to be set up.

## Setting the PHP for the Subdomain
If your cPanel does NOT have a Software Section with a selection of MultiPHP Manager, you may need your host’s help on this step.

If you don’t have MultiPHP Manager, ask your host to set the PHP for the `test` folder that you created.  (Emphasize that it is above webroot, i.e. in `/home/YOURACCOUNT/test`.)

If you do have MultiPHP Manager, go to the Software Section in the cPanel and open MultiPHP Manager. Set the PHP version appropriately.

If `test.YOURSITE.com` is not already listed with the needed version of PHP, select the box in front of `test.YOURSITE.com` and select a version of PHP in the drop-down titled PHP Version above the listing area.

The PHP version you select should be the latest supported version that works with your version of Zen Cart. The PHP Version Matrix will show you the versions of PHP that work well with the version of Zen Cart you are testing.

For instance, with Zen Cart 1.5.8a, you could use PHP 7.4, 8.0, 8.1 or 8.2.  (See [Server Requirements for running Zen Cart](/user/first_steps/server_requirements/#php-version) for other versions.)

## Installing your new version

Upload your software to the folder `/home/YOURACCOUNT/test.YOURSITE.com/`. Be sure the two `configure.php` files use this folder as `DIR_FS_CATALOG`, and that all of the `HTTP*_SERVER` settings use the subdomain URL, not the main domain URL.  For example, 

```
define('HTTPS_SERVER', 'https://test.YOURSITE.com');
```

## SSL 
You may need to take steps at this point to get your SSL certificate for your new subdomain.  On cPanel, go to SSL/TLS Status, select your new domain and run AutoSSL.

## Configure Files 

You'll have to tweak your configure files as shown below. 

### includes/configure.php 
```
define('HTTP_SERVER', 'https://test.YOURSTORE.com');
define('HTTPS_SERVER', 'https://test.YOURSTORE.com');
define('DIR_FS_CATALOG', '/home/YOURACCOUNT/test/');
```

### admin/includes/configure.php 

```
define('HTTP_SERVER', 'https://test.YOURSTORE.com');
define('HTTP_CATALOG_SERVER', 'https://test.YOURSTORE.com');
define('HTTPS_CATALOG_SERVER', 'https://test.YOURSTORE.com');
define('DIR_FS_CATALOG', '/home/YOURACCOUNT/test/');
```

And both files will probably have 

```
define('DIR_WS_CATALOG', '/');
define('DIR_WS_HTTPS_CATALOG', '/');
```

since you've put the files in the `test` folder just above webroot, rather than a subfolder under `test` (even if your live store is in a subfolder). 

