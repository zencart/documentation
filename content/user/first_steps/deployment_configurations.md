---
title: Basics - Deployment Configurations
description: Ways to install Zen Cart 
category: first_steps
weight: 10
---

There are different ways to install Zen Cart, depending on your needs. 
Any of these are legitimate deployments. 

Please be sure you're familiar with [basic terms in Zen Cart](/user/first_steps/basic_terms/) prior to reading this FAQ.

## 1. Cart in root of store 

The configuration that is assumed throughout the Storeowner Docs is that you have installed Zen Cart in the root of your hosting account.

Your store URL would be `https://www.YOURSTORE.com/` (or `https://www.YOURSTORE.com/index.php`). 

Your files would be under the `public_html` folder in your hosting account. 

## 2. Cart in root of store, blog in subfolder

This is very common for people who want the kind of additional content management capabilities offered by a blog (or other tool).

The cart is the same as the prior example.

The blog would be addressed by appending its folder name to the store URL.

Your store URL would be `https://www.YOURSTORE.com/` (or `https://www.YOURSTORE.com/index.php`). 

Your blog URL would be `https://www.YOURSTORE.com/blog/`. 

This would also apply for a forum in a subfolder, CMS in a subfolder, etc. 

**Please note:** Exercise caution when adding software on top of your Zen Cart installation.  See the [blogging FAQ](/user/running/blogging).
 
## 3. Existing website in root of store, cart in subfolder

If you have an existing website, and you'd like to add ecommerce, you can put your store in a subfolder.  We'll use the generic name `YOURSUBFOLDER` but the real name you use would likely be `store` or `shop`. 

Your store URL would be `https://www.YOURSTORE.com/YOURSUBFOLDER` (or `https://www.YOURSTORE.com/YOURSUBFOLDER/index.php`). 

Your files would be under the `public_html/YOURSUBFOLDER` folder in your hosting account. 

## 4. Nothing in root of store, cart in subfolder 

Even if you don't have an existing website in the root folder, you can still place your cart in a subfolder.   The URL and file placement are like the previous case.  In this case, you'll want an `.htaccess` file to redirect anyone who comes to the root folder to the subdomain.  

As an example, if your subfolder were called `store`, you would do this: 

```
RewriteEngine On
RewriteRule ^index\.php$ /store/ [L]
```

For instructions on moving your cart from the root to a subfolder (or vice versa), see [moving your Zen Cart folder](/user/installing/move_cart/).

