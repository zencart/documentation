---
title: Download folder - Securing 
description: Zen Cart Download folder - Securing 
category: security
weight: 10
---

In a Windows-hosting environment, when you create a virtual product using download attributes customers are able to download a product as much as they like by using the following as an example:   www.websitename.co.uk/download/product.zip  

Download by redirect (which windows servers can't usually provide) is much more secure than without redirect.  

However, it's true that if a user understands Zen Cart infrastructure, they could perhaps figure out how to download directly from the "downloads" folder.  

Given that scenario, the following options are available:  

1\. Zen Cart already provides .htaccess protection for that folder. You could (should) update that file to add the file-extensions for all the types of files in your downloads folder. Thus, people using a browser cannot directly access any files matching those extensions. Granted, if you have redirect off, this may pose a problem. And of course, only works if .htaccess is fully supported on your server. (ie: not on Windows hosts)  

2\. If you are using redirect or streaming then moving the "downloads" folder into a place outside your webroot will prevent anyone from ever accessing the files with a browser unless they are using the Zen Cart-supplied links in their order details.  This is the most secure approach. It requires physically relocating the folder, and editing your configure.php files to point to the real location of your downloads folder so that Zen Cart has a clue where to find the files it will be streaming to your users.  This works on both Windows and Linux/Unix hosts.  
See the related FAQ on [How To Relocate my Download folder outside my webroot for better security](/user/security/relocate_download_folder)  

Apart from securing your downloads folders/files, Zen Cart also only offers a limited number of download attempts per order, preventing customers from sharing usable links with their friends.  You can configure the counters and even reset individual downloads again via the admin interface.
