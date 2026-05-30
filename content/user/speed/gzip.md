---
title: GZIP compression
description: Compressing pages during delivery 
category: speed
weight: 10
---

## Modern Webservers Support Output Compression By Default
You probably don't need to do anything for compression tuning. But, you should check the following with your hosting company:

If you want compressed responses, enable gzip or Brotli in your web server or CDN for text-based content such as HTML, CSS, JavaScript, JSON, XML, and SVG.

Do not enable compression for file types that are already compressed, such as ZIP, JPEG, PNG, WebP, MP4, and PDF.

If you use shared hosting, contact your hosting provider and ask them to enable server-level compression for your site.

Another way to check is to type your URL into [this http-compression-test website](https://www.whatsmyip.org/http-compression-test).  If it says your domain "IS GZIPPED" then you're good to go. If not, talk to your hosting provider.


## For Older Zen Cart versions
(The following was available within Zen Cart up until v3.0.0, because it supported older Webserver technologies which often weren't tuned well for compression):

GZIP Compression is a technology that allows your webserver to reduce the size of pages before being transmission from server to browser.
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

Another way to check is to type your URL into [this http-compression-test website](https://www.whatsmyip.org/http-compression-test).  If it says your domain "IS GZIPPED" then you can leave the setting at 0 in Zen Cart.

