---
title: Basic Terms 
category: first_steps
weight: 10
---

This page explains some terms you will see throughout the documentation site
 that are used as variables to represent site specific path information. 

### YOURSITE

The variable `YOURSITE` is used to to represent your domain name, and thus
to show the path to access your site over the web.  If your site is 
called "John Doe Tools" and your domain is "JohnDoeTools.com", then 
`http://www.YOURSITE.com` really means `http://www.JohnDoeTools.com`. 

**Note:**  If you wish, you may install your Zen Cart in a subfolder under your `public_html` folder. For example, the site above could be stored in 
`/home/johndoe/public_html/shop/`, which would make the URL 
`http://www.JohnDoeTools.com/shop`. 

However, for the sake of simplicity, the explanations on this site assume you did not do this.  Don't get hung up on the fact that an article will say 
`http://www.YOURSITE.com` rather than `http://www.YOURSITE.com/YOURSUBFOLDER/`  - 
it was a decision made for simplicity and consistency.  If your site is 
in a subfolder, just add on the `/YOURSUBFOLDER/` whereever it is needed as you are reading. 

Common values for `YOURSUBFOLDER` are `site`, `shop`, `cart` or `store`. 
Using a subfolder is especially appropriate if you have a large, built-out
website, and Zen Cart is being used to add-on ecommerce functionality 
(rather than to provide your entire website). 

### YOURTEMPLATE 
To allow you to customize the appearance of your site, Zen Cart has a 
templating capability.  Names of templates vary, so they are 
referred to in this document with the variable `YOURTEMPLATE`.  

So if your template is `responsive_sheffield_blue`, then when you read 
`YOURTEMPLATE`, just think `responsive_sheffield_blue`.  So the folder 

`includes/templates/YOURTEMPLATE/templates/` 

would be 

`includes/templates/responsive_sheffield_blue/templates/` 

in your cart. 

### YOURLANGUAGE 
If an article has multilanguage dimensions, the variable `YOURLANGUAGE` 
will be used to refer to language specific folders. 

For English language only stores, the path 

`/includes/languages/YOURLANGUAGE/`

is just 

`/includes/languages/english/`

### YOURSITEFOLDER 
The variable `YOURSITEFOLDER` is used to refer to the folder in your hosting 
account which holds your site's files.  A very common setup is the following,
assuming your account name is `johndoe`: 

* `/home/johndoe/public_html/` - the top level directory your webserver 
can access. 

Everything will be under `YOURSITEFOLDER` when you view files, either in FTP or in your CPanel's File Manager. 

