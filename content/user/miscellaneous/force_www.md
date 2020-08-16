---
title: How can I force my site to add "www." to the URL? 
description: URL rewrite to add www subdomain for Zen Cart
category: miscellaneous
weight: 10
---
**Scenario:**

Customer types in `YOURSITE.com` when trying to enter your website.

In most cases this will let them get to your site fine.

BUT, if you've configured your site to use `www.YOURSITE.com` in all the URLs it generates, then the customer's next click will attempt to change the URL and (on some servers) may log them out if they were attempting login, etc.  

There are a couple things to keep in mind to handle this:

- Always be consistent in your use of your domain name.  If you're going to use `www.YOURSITE.com`, be sure to use it exactly that way everywhere. Don't drop the `www.` unless  you do it consistently in all places.
- In your SSL certificate, when you register one, you must specify a domain name. Again, be consistent. If you're using `www` in your URL, use it in your SSL certificate too.
- Ensure that your hosting company has configured a  `www` address as an alias to your domain name so that "both" will work -- otherwise visitors might get a "domain not found" error instead of your site.
- If you are running on an Apache webserver, you can set up a `.htaccess` rule to automatically add the `www` into the URL if the customer forgets to include it. The following is what you'd put in your `.htaccess` to accomplish this:

```
RewriteEngine On
RewriteCond %{HTTP_HOST} ^YOURSITE.com$
RewriteRule ^(.*)$ http://www.YOURSITE.com/$1 [R=301,L]
```
