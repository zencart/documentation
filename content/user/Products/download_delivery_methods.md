---
title: Download delivery methods 
description: Zen Cart Download delivery methods 
category: products
weight: 10
---
For downloadable products, there are several ways of delivering downloadable content to your customers, depending on your hosting configuration.  

You can find these options in **Admin->Configuration->Attribute Settings**:  

## Download by Redirect

**Download by Redirect ... when set to True** ... uses the Linux/unix "symlink" feature to create a temporary file "stub" in the /pub folder. Then your customer is directed to that file-stub for their download. This means the customer can only ever access it via that stub, which disappears after their download is over. It hides the "real" location of the file so they can't just share the download link with their friends and have them steal your downloads for free.  

This option only works on Linux hosts.  On Windows hosts this option will not work because Windows doesn't support symlinks, at least not via PHP.  

This option requires that the "pub" folder be set to read-write permissions ... typically 777 (or 755 on suexec hosts).

This method is not affected by PHP `max_execution_time` limits.  

## Download without Redirect

If **Download by Redirect is set to False**, then the download link given to the customer is the direct link to the file in your /download folder ... meaning they can download as often as they want and share the link with their friends ... potentially letting folks steal your downloads.   
_This option has its security limitations, but works on both Windows and Linux hosts._  
This method is not affected by PHP max_execution_time limits.  

## Download by Streaming

**Download by streaming** only works _when Download by Redirect is off._ Instead of giving the customer a URL to the file, Zen Cart sends the file as a download, in 2KB chunks. This helps with server RAM load as well as completely preventing any download link from ever being shared with your customers.  
This option works on both Windows and Linux hosts.  
There is one limitation with this method ... your server's PHP configuration for `max_execution_time` needs to be set to a value large enough for your largest file to complete its download, or at least configured in such a way that Zen Cart is allowed to override it. 
Zen Cart attempts to set it to unlimited when the download starts, but if your server won't allow that, it'll default to the server's master setting ... which is often 30 seconds.

