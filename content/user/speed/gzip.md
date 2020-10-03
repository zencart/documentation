---
title: GZIP compression
description: Compressing pages during delivery 
category: speed
weight: 10
---

GZIP Compression is a technology that allows your webserver to 
reduce the size of pages before being transmission from server to browser.
This speeds the delivery of web pages. 

### When to Use It
If PHP is already configured on the server with `output_buffering` enabled, then it is already doing this compression before transmission. 
This means that if you turn on GZip compression in Zen Cart, you're 
doing compression twice, which can actually can slow things down.

To check whether your server's PHP configuration already does this, go to 
[Admin > Tools > Server/Version Info](/user/admin_pages/tools/server_info/). 
Search the page for `output_buffering` and determine its setting.
If it is "On" or a number greater than "0", leave the Zen Cart GZip setting set to 0.  
If it is Off" or "0", set enable [GZIP in Zen Cart](/user/admin_pages/configuration/configuration_gzipcompression/). 

Another way to check is to type your URL into [this website](http://www.whatsmyip.org/http-compression-test).  If it says your domain "IS GZIPPED" then you can leave the setting at 0 in Zen Cart.

