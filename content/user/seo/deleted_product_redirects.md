---
title: Deleted product redirects
description: Using .htaccess redirects for deleted products 
category: seo
weight: 10
---

.htaccess rules are very powerful/flexible and so can be daunting at first.  
When you delete a product, external links to that product will fail as not found "404". This is something you want to avoid as you lose those long-established inward links.  
To prevent that, and to automatically inform and update the requesting server links requires a 301 code to be returned and a redirect to the new url you wish be used as a the permanent replacement.

# Example "Redirect"
The old/obsolete product url:  
www.mysite.com/index.php?main_page=product_info&cPath=1_5963&products_id=8263

The new product url:  
www.mysite.com/index.php?main_page=product_info&cPath=1_5963&products_id=9015

In .htaccess, add:  
>Redirect 301 www.mysite.com/index.php?main_page=product_info&cPath=1_5963&products_id=9015 www.mysite.com/index.php?main_page=product_info&cPath=1_5963&products_id=8263

Note you are trapping the entire url, returning a 301 to the requesting server and redirecting to another complete url.

However, if there are already “RewriteRule” commands in the same file, these will be processed *first*, which can be very confusing if they match your url first so you think your redirect is not working.  
In this case you should use a RewriteRule instead of a Redirect to prevent confusion.

# Example "Rewrite"
The old/obsolete product url is just the stub:  
www.mysite.com/index.php  
and the rest is the query string:   main_page=product_info&cPath=1_5963&products_id=8263

So to redirect this with a RewriteRule requires a RewriteCond to match the query string:  
>RewriteCond %{QUERY_STRING} ^.*products_id=8263$  
RewriteRule ^index\.php$ /index.php?main_page=product_info&cPath=97&products_id=9015 [R=301,L]

In this example, note the following about RewriteCond:   
`^` - start of the string to match  
`.*` - is any number of any characters. You could use more of the query string, but using this means it captures urls with different or missing cPaths.  
`products_id=8263` - is the part you want to match  
`$` - the end of the string, meaning that products_id=8263 is at the end of the string.

In the RewriteRule,  
`^` - start of the url to match. Note the url is index.php, nothing else.  
`\.` – the backslash is just escaping the decimal point  
`$` - the end of the url  
`/index.php?main_page=product_info&cPath=97&products_id=9015` - the destination on the same server  
`[R=301,L]` – 301 is the code to return to the server, L means it’s the last rule/don’t process any more rules for the RewriteCond above it. 



