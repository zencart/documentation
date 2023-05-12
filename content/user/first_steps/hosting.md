---
title: Basics - Hosting and Domain concepts
description: Domains, Name Servers, Hosting and more 
category: Installing
weight: 10
---

### Domains

- A **domain** is the mnemonic name of your website.  It provides an
easy-to-remember address that is used in place of the IP Address where
your website is hosted. Using the example 
from [Basic Terms](/user/first_steps/basic_terms/), your domain would be 
`JohnDoeTools.com`.  Domain names are leased for a specific time 
interval, generally between 1 and 5 years.  After this time, you 
must renew your domain or it will go back on the market. 

The domain name includes a TLD or "top-level-domain".  The most common
TLD in the United States in the commercial space is `.com`, but many 
other TLDs are available, including country specific TLDs (`.co.uk` for the 
United Kingdom, for example). 

- A **domain registrar** keeps your domain.  Popular domain registrars 
include GoDaddy, NameCheap, and Network Solutions.  

    If a domain is *not* owned by someone else, you may simply buy it 
from a registrar for a small fixed fee.  Then you just have to renew it
every so often, and it's yours for the life of your business. 

    If a domain *is* owned by a third party but not in use, they *may* be willing to sell it to you
(generally through an escrow agent like Sedo or Afternic), but
it will be significantly more expensive.   Your best choice in a case like 
this may be to go with a different TLD (`JohnDoeTools.net`), 
a different spelling of your name, perhaps adding hyphens or adding/removing
a plural (`JohnDoe-Tools.com`, `JohnDoeTooling.com`), or a 
different name entirely (`ToolsFromJohnDoe.com`). 

- **Registrar Transfer** is the process of moving your domain name
from one registrar to another.  

    Contact information is used to confirm any requested changes to domain registration info, including change of registrar, and renewals.

    If you're thinking of transferring your domain to a new Registrar, you need to:

    *   unlock the domain to allow Domain Transfer
    *   authorize the transfer by confirming the email sent to your domain's Administrative Contact
    *   pay the one-year-renewal fee (which buys you one more year after your current expiry date) to complete the transfer, based on the fee set by the registrar you're transferring to.
<br />   <br />

- **DNS** is a system of computers that maintain a directory of 
domain name to IP Address mappings. 


### Name Servers

A name server converts a name to an IP Address.  Your nameservers 
(there are generally two) are values you specify in your 
domain registration with your registrar, and they point (generally)
to your hosting company.  As an example, the nameservers for 
A2 Hosting's shared accounts are called 
`ns1.a2hosting.com` and `ns2.a2hosting.com`.

If you decide to change hosting companies, you will have to update
your name server settings at your domain registrar.  This change 
will take some time to ripple through the system - the guidance is
24 to 48 hours, but it often takes less.  Just be prepared for
some downtime. 

### Hosting Companies

Your hosting company (or *hoster* or *website host*) is the company that provides server space 
for you to run your website.  You will pay monthly or annually 
for this service. 

Hosting accounts are offered in two flavors: 

* Shared Hosting - You share server space with other accounts.

* Virtual Private Server (VPS) Hosting - You have your own isolated server space. 

VPS is more expensive but more secure and provides greater flexibility. 

Hosting accounts also offer different OS versions.  The
Zen Cart project recommends Linux with Apache (or Linux with Nginx),
but **not** Windows with IIS. 

Most users will want a hosting account that offers a Control Panel, such
as cPanel.  The control panel gives you easy access to the underlying 
operating system functionality. 

The Zen Cart project recommends a number of hosting providers on 
their [Recommended Services](https://www.zen-cart.com/content.php?3-services) page.

If you haven't yet selected a hoster, please read [picking a hoster](/user/installing/pick_hosting/).

### Webserver 

The word *webserver* (or *web server*) can mean different things based on context. 
Sometimes when people use this word, they mean the computer associated with your 
hosting account that runs your website.  And sometimes, they mean the 
piece of software that *runs* on the computer associated with your 
hosting account, which *serves* up web pages.  

Here, we are using the second meaning. 
For programs like Zen Cart, running on commercial hosters, 
there are three main options for webserver software: 

- Apache (runs on Linux)
- Nginx (runs on Linux)
- IIS (runs on Windows)

The Zen Cart team recommends Apache or Nginx, **not** IIS.

### FTP 
You will need to use an [FTP Tool](/user/first_steps/useful_tools/#ftp-tools)
to transfer files between your computer and your server.  
An example of transferring a file is provided in [Installing a File](/user/new_user_topics/no_such_file/#installing-a-file). 

### cron 

Cron is a utility on Linux hosting accounts that allows you to automatically schedule jobs to run at specific intervals.  An example of a job you might want to run is the [exchange rate updater](/user/admin_pages/localization/currencies/#update-currencies). 

Facilities for setting up cron jobs vary; contact your hoster for details. 

### SSL Certificates

An SSL certificate allows your content to be securely accessed 
using encryption.  

When an SSL Certificate is purchased, it is issued to a particular domain name. Certificates are purchased in 1-year blocks. The certificate is installed on your Hosting Server and linked to your site so that your customers can shop with encryption protection when needed. Some hosting companies offer free SSL certificates with certain plans. Check the [Recommended Services](https://www.zen-cart.com/content.php?3-services) page to see which of our recommended hosts provides free SSL certificates.

SSL Certificates are an add-on to a hosting account, and are not directly tied to a hosting plan's expiry dates, etc. However, since hosting plans are usually purchased first, and SSL certificates are issued a few days later, it is quite common for a hosting plan to expire a couple days before an SSL certificate expires.

Certificates cannot be directly transferred to another host due to the public/private key generation systems. This is primarily to protect you against theft of identity or the certificate. To move an existing certificate to another server requires that the Issuer (whoever you bought the certificate from originally) re-issue the certificate tied to the new private/public key of your new hosting server, sometimes for a nominal re-issuance fee. Thus, it's simplest to issue certificates around the same time as switching hosting from one place to another.

Certificates can be issued for `www.`, `non-www.`, or wildcard. Some hosters recommend not using wildcard.

It is important to know which way your certificate is issued. Settings in the `configure.php` files that address `https://` need to match the form of your SSL to prevent possible log in problems. If your SSL is for `www.`, then the settings should show `https://www.YOURSITE.com`.  If `non-www.`, the settings should show `https://YOURSITE.com`.

For more information on SSL, see these articles: 

* [What is an SSL certificate?](/user/security/ssl_cert/)
* [How do I enable SSL?](/user/installing/enable_ssl/)
