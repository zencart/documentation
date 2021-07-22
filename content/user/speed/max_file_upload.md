---
title: File upload limitations 
description: Dealing with post_max_size and max_file_uploads 
category: speed
weight: 10
---

Note: This does not apply to your site unless you use File Upload attributes on products. 

The ability to upload files to your Zen Cart site via a browser is affected by several factors:

### PHP Limits on your Server
Your hosting company has configured your server with certain capabilities and limitations. The default configuration for PHP uploads is often set at just 2 MB.  Some hosting companies increase this. Some do not.
It is controlled by the following settings in `php.ini` (which you may or may not have control over):

- post_max_size
- max_file_uploads

Both of these need to be bigger than the largest file size you want to upload.

### PHP Timeout Limit on your Server
The speed of the internet connection between your (or your customer's) computer and your webserver will affect how long it takes to upload files. 
So, in addition to the size limits, there's also the time required to actually *do* the upload.
The following settings control the length of time PHP is allowed to wait for an action to complete, including uploading on a page:

- max_execution_time
- max_input_time

Both of these need to be long enough (in seconds) for the time required for the slowest likely connection to upload the largest likely filesize.

### Changing these PHP Settings
It's best if those settings can be configured in the server's master PHP settings, or at least in the hosting-account's settings (if not in a control panel, then at least in a custom `php.ini` activated for just that user).  Some of those settings can be set in code while the PHP script is executing. Check with your hosting company about the best way to change these settings for your unique needs.  Some hosts do NOT allow you to change these; if yours does not, you may wish to change hosters.

See [PHP Configuration](/user/upgrading/php_configuration/) for more details. 

### Zen Cart Admin Limit
In your Zen Cart [Admin > Configuration > Maximum Values](/user/admin_pages/configuration/configuration_maximumvalues/) screen, you'll find a *Maximum Upload Size* parameter. This is the number (in bytes) that Zen Cart checks to see if the file uploaded is small enough to suit maximum requirements. If the uploaded file is larger than this number, it will be rejected.

**NOTE:** This number is ignored if the PHP limits discussed above are smaller, since PHP will reject the upload if the file is too large, long before Zen Cart will be able to check it using its own values.

