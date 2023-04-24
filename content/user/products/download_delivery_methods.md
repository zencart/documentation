---
title: Download delivery methods 
description: How are downloads made available after checkout? 
category: products
weight: 10
---
For [downloadable products](/user/products/downloadable/), there are several ways of delivering downloadable content to your customers, depending on your hosting configuration.  

You can find these options in [Admin > Configuration > Attribute Settings](/user/admin_pages/configuration/configuration_attributesettings/):

## Serving files from your own store's webserver

### Download by Redirect

**Download by Redirect - when set to True** uses the Linux/UNIX "symlink" feature to create a temporary file "stub" in the /pub folder. Then your customer is directed to that file-stub for their download. This means the customer can only ever access it via that stub, which also disappears after their download is over. 

This approach hides the "real" location of the file so customers can't just share the download link with others and have them steal your downloads for free.

This option works well on Linux hosts. Many older Windows hosts using older PHP versions don't support symlinks.

This option requires that the "pub" folder be set to read-write permissions, typically 755.

This method is not affected by PHP `max_execution_time` limits.  

This approach can be problematic if several people buy and download the same thing at the same time, because there's some garbage-collection that cleans up symlinks, and if that happens during someone's download, the cleanup could break the download.

For statistics or analytics, your Apache/Nginx logs may give you more insights about download-by-redirect downloads. You won't find those in PHP logs.

### Download without Redirect

If the earlier setting above **Download by Redirect is set to False**, then the download link given to the customer is the direct link to the file in your `/download` folder, meaning they can download as often as they want and share the link with others, potentially letting people steal your downloads.   

_This option has its security limitations, but works on both Windows and Linux hosts._  

This method is not affected by PHP `max_execution_time` limits, and activity will not be in PHP logs (but will be in Apache/Nginx logs).

### Download by Streaming

**Download by streaming** only works _when Download by Redirect is off._ Instead of giving the customer a URL to the file, a PHP process will read the file in small increments (4K chunks) and serve those out as a stream of data until done. 

From a security perspective this completely prevents any download link from ever being shared with non-customers, because it requires customers to download only from a logged-in account session via their order-history page.

This option works on both Windows and Linux hosts.  

There is one limitation with this method: the PHP `max_execution_time` setting needs to be set to a value high enough to allow for your largest file to complete its download. Zen Cart attempts to set the time to 25 minutes, but some servers have a master setting that prevents Zen Cart from overriding this. (PHP's default is often 30 or 60 seconds.)



## Serving files from "the cloud" (remote URLs)

Since v1.5.6 you can optionally serve downloadable products/files via external services such as AWS, Dropbox, Google Drive, etc, instead of hosting them on your own store's webserver.

### Serving files via a URL such as sharing Dropbox links

In the Attributes Controller or Downloads Manager you can specify a URL instead of a filename. If the "filename" starts with `https://` then it will be treated as a remote URL.

You may optionally specify a file size like this: `https://example.com/filename.ext:number_of_bytes`. This size helps browsers display some indication of download progress, and is also displayed next to the download button.

Remember that URLs like this offer NO protection against theft: once the link is given to a customer they can give the link to anyone else and download again.

TIP: If using Dropbox links for your file URLs, change the `&dl=0` to `&dl=1` on the "sharing link" that Dropbox gives you. This will make the download happen immediately, instead of the customer seeing the file open on the Dropbox website.

Similarly, when sharing URLs from other cloud-storage services, ensure that the "sharing link" you're using is secure.

Be sure to **test the link** in a "private browsing mode" or "incognito mode" browser session to verify both that the link works and that you're not giving "too much permission" (such as accidentally sharing a google-docs page in "edit" mode).


### Serving files via AWS

You may wish to use Amazon S3 to host your downloads.

After setting up your AWS credentials (described below), simply give `aws:bucketname/filename.ext:number_of_bytes` as the filename in attributes controller. 

The optional `:number_of_bytes` part is the file size which will be displayed to the customer and allows for download-progress to be detected by the browser.

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

When sharing AWS links like this, a security token is added to the download-URL generated by your store when the customer clicks the Download link/button in their Order History. This limits the number of times the customer can download the product, and prevents unauthorized downloads.


### Alternatives

To enable secured downloads via other 3rd party cloud providers, cloning the `/includes/classes/observers/auto.downloads_via_aws.php` file is a good starting-point to build an integration to another provider's API.




