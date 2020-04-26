---
title: Download delivery methods 
description: Zen Cart Download delivery methods 
category: products
weight: 10
---
For downloadable products, there are several ways of delivering downloadable content to your customers, depending on your hosting configuration.  

You can find these options in [Admin > Configuration > Attribute Settings](/user/admin_pages/configuration/configuration_attributesettings/):

## Download by Redirect

**Download by Redirect - when set to True** uses the Linux/UNIX "symlink" feature to create a temporary file "stub" in the /pub folder. Then your customer is directed to that file-stub for their download. This means the customer can only ever access it via that stub, which disappears after their download is over. It hides the "real" location of the file so they can't just share the download link with others and have them steal your downloads for free.  

This option only works on Linux hosts.  On Windows hosts this option will not work because Windows doesn't support symlinks, at least not via PHP.  

This option requires that the "pub" folder be set to read-write permissions, typically 777 (or 755 on suexec hosts).

This method is not affected by PHP `max_execution_time` limits.  

This approach can be problematic if several people buy and download the same thing at the same time, because there's some garbage-collection that cleans up symlinks, and if that happens during someone's download, the cleanup could break the download.

Your Apache/Nginx logs may give you more insights about download-by-redirect downloads. You won't find those in PHP logs.

### Serving files via a URL such as sharing Dropbox links

If using Dropbox links for your file URLs, change the `&dl=0` to `&dl=1` on the "sharing link" that Dropbox gives you. This will make the download happen immediately, instead of the customer seeing the file open on the Dropbox website.

### Serving files via AWS

If you have set up your AWS credentials, when you configure your product attributes to specify a filename, simply give `aws:bucketname/filename.ext` as the filename in attributes controller.

To set your AWS credentials, create an `/includes/extra_datafiles/dev-aws_credentials.php` file containing the following:

```php
<?php
if (!defined('IS_ADMIN_FLAG')) die('UNAUTHORIZED');

// AWS website: https://console.aws.amazon.com
// Use the AWS console's IAMS screen to create a user for downloading your S3 files.
// Copy the Access Key and Secret and insert them as shown, below:
define('AMAZON_S3_ACCESS_KEY', 'your aws access key id here');
define('AMAZON_S3_ACCESS_SECRET', 'your aws secret here');

```

## Download without Redirect

If **Download by Redirect is set to False**, then the download link given to the customer is the direct link to the file in your /download folder, meaning they can download as often as they want and share the link with others, potentially letting people steal your downloads.   

_This option has its security limitations, but works on both Windows and Linux hosts._  

This method is not affected by PHP max_execution_time limits.  

## Download by Streaming

**Download by streaming** only works _when Download by Redirect is off._ Instead of giving the customer a URL to the file, Zen Cart uses on a PHP process to read the file in small increments (4K chunks) and serve those out as a stream of data until done. It's intended to bypass memory limits imposed by your server config especially when dealing with very large files. It also increases the max duration time of the download to 25 minutes (if your server's PHP hasn't been configured to disallow that).

This method helps with server RAM load as well as completely preventing any download link from ever being shared with your customers.  

This option works on both Windows and Linux hosts.  

There is one limitation with this method: your server's PHP configuration for `max_execution_time` needs to be set to a value large enough for your largest file to complete its download, or at least configured in such a way that Zen Cart is allowed to override it. 

Zen Cart attempts to set it to unlimited when the download starts, but if your server won't allow that, it'll default to the server's master setting, which is often 30 seconds.

