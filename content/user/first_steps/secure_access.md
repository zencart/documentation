---
title: Basics - Secure Access 
description: Secure Access to your Zen Cart 
category: first_steps
weight: 10
---

## Having an SSL certificate 

Yes, you do need an SSL certificate; it's part of running an online store. It doesn't matter that you don't do onsite credit card collection; [you still need an SSL certificate](/user/first_steps/yes_you_need_ssl/).

**Don't let this be you!**

<img src="/images/insecure_cart.png" alt="Insecure cart" width="50%" />

## Secure File Transfer 

**Do not** use plain FTP to access your server's files.  

Although this was a common way to do it back in 2003, it is no longer a good practice, since it is not secure. 

Some secure options are:

- FTPS
- SFTP
- Require explicit FTP over TLS

Availability of these specific options is hoster-dependent but at least one
of them should be available. 

If your hosting company does not offer some mechanism for secure file transfer, then they are most likely not PCI Compliant either, and you should be choosing a different hosting company who takes security seriously.

## Secure access to your Admin

Be sure your `admin/includes/configure.php` file has all URL settings using `https`.  This includes `HTTP_SERVER`, `HTTP_CATALOG_SERVER` and `HTTPS_CATALOG_SERVER`, and if it exists, `HTTPS_SERVER`. 

Use an admin username other than `admin` (or `nimda`).  Make it hard to guess.

## Secure cPanel Access 

Just because you run an SSL on your site doesn't mean your cPanel access is secure.  Look for the padlock in your browser's address bar, and tell your hoster to fix it if it's not there! 

**Don't let this be you!**

<img src="/images/insecure_cpanel.png" alt="Insecure cPanel" width="40%" />

