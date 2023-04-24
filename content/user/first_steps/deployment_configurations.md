---
title: Basics - Deployment Configurations
description: Ways to install Zen Cart 
category: first_steps
weight: 10
---

There are different ways to install Zen Cart, depending on your needs. 
Any of these are legitimate deployments. 

Please be sure you're familiar with [basic terms in Zen Cart](/user/first_steps/basic_terms/) prior to reading this FAQ.

For instructions on moving your cart from the root to a subfolder (or vice versa), see [moving your Zen Cart folder](/user/installing/move_cart/).

For clarity, we will use the folder names `store` for the cart in a subfolder, and `blog` for the blog (or other web application) in a subfolder, although of course any other folder names could be used. 

## Deployment Model 1: Cart in root 

```
Cart URL: https://www.YOURSTORE.com 
```

The configuration that is assumed throughout the Storeowner Docs is that you have installed Zen Cart in the root of your hosting account.

Your files would be under the `public_html` folder in your hosting account. 

## Deployment Model 2: Cart in root, blog in subfolder

```
Cart URL: https://www.YOURSTORE.com 
Blog URL: https://www.YOURSTORE.com/blog 
```


This is very common for people who want the kind of additional content management capabilities offered by a blog (or other tool).

The cart is the same as the prior example.

The blog would be addressed by appending its folder name to the store URL.

This would also apply for a forum in a subfolder, CMS in a subfolder, etc. 

**Please note:** Exercise caution when adding software to your Zen Cart installation.  See the [blogging FAQ](/user/running/blogging).
 
## Deployment Model 3: Existing website in root, cart in subfolder

```
Website URL: https://www.YOURSTORE.com/
Cart URL: https://www.YOURSTORE.com/store  
```

If you have an existing website, and you'd like to add ecommerce, you can put your store in a subfolder.  

Your files would be under the `public_html/store` folder in your hosting account. 

See [Subfolder Names](#subfolder-names) below.

## Deployment Model 4: Empty root, cart in subfolder 

```
Cart URL: https://www.YOURSTORE.com/store  
```

Even if you don't have an existing website in the root folder, you can still place your cart in a subfolder.   The URL and file placement are like the previous case.  In this case, you'll want an `.htaccess` file to redirect anyone who comes to the root folder to the subdomain.  

As an example, if your subfolder were called `store`, you would do this: 

```
RewriteEngine On
RewriteRule ^index\.php$ /store/ [L]
```
### Subfolder Names

**Please note:** Do not use the Zen Cart version as the subfolder name.  
For example, do not put your site in `https://www.YOURSITE.com/zen155e` or `https://www.YOURSITE.com/zc154/`. The reasons for this are as follows: 

- You will eventually upgrade your site, and then the folder name and actual version will not match, which will be confusing.  And changing the subfolder name will break any inbound links you have.
- If you delay upgrading your site after new releases are made, you are advertising the fact that your site software is old, which can tempt bad guys to probe for vulnerabilities. 


## Deployment Model 5: (Advanced) Separate subdirectories for different versions

Technical staff with advanced server understanding may prefer to use version-numbered directories for their Zen Cart folder, and then redirect the site's DocumentRoot setting to point to the versioned-subdirectory either by editing a vhost configuration or using a symlink. This can be convenient for staging upgrades that allow for near-zero downtime, and also very convenient downgrading if a problem were to occur. This is a strategy that should only be used by someone with advanced understanding of Zen Cart and how server vhost configurations and symlinks work.
