---
title: Basics - Terms and Definitions
description: Terms used throughout this site 
category: first_steps
weight: 10
---

This page explains some terms you will see throughout the documentation site
 that are used as variables to represent site specific path information. 

You may also wish to browse the [glossary](/user/first_steps/glossary/).

### YOURSITE

The variable `YOURSITE` is used to to represent your domain name, and thus
to show the path to access your site over the web.  If your site is 
called "John Doe Tools" and your domain is "JohnDoeTools.com", then 
`http://www.YOURSITE.com` really means `http://www.JohnDoeTools.com`. 

**Note:**  If you wish, you may install your Zen Cart in a [subfolder](/user/installing/subfolder/) under your `public_html` folder. For example, the site above could be stored in 
`/home/johndoe/public_html/shop/`, which would make the URL 
`http://www.JohnDoeTools.com/shop`.  See [deployment configurations](/user/first_steps/deployment_configurations) for a description of possible approaches.  

However, for the sake of simplicity, the explanations on this site assume you did not do this.  Don't get hung up on the fact that an article will say 
`http://www.YOURSITE.com` rather than `http://www.YOURSITE.com/YOURSUBFOLDER/`  - 
it was a decision made for simplicity and consistency.  If your site is 
in a subfolder, just add on the `/YOURSUBFOLDER/` wherever it is needed as you are reading. 

Common values for `YOURSUBFOLDER` are `site`, `shop`, `cart` or `store`. 
Using a subfolder is especially appropriate if you have a large, built-out
website, and Zen Cart is being used to add-on ecommerce functionality 
(rather than to provide your entire website). 

**Please note:** Do not use the Zen Cart version as the value for `YOURSUBFOLDER`.  For example, do not put your site in `https://www.YOURSITE.com/zen155e` or `https://www.YOURSITE.com/zc154/`. 
The reason for this is that your Zen Cart version will change over time when the site gets updated, and it will be confusing to have your Zen Cart 1.5.8 installation in a folder called `zc154` or `zen155e`.
See [deployment configurations](/user/first_steps/deployment_configurations#subfolder-names) for more information.

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

You will see lots of different variables used in place of `YOURTEMPLATE` - 
we have just chosen this for consistency.  Some people will instead call 
this `YOUR_TEMPLATE`, or `custom` or `YOUR_CUSTOM_TEMPLATE` - but it's all
the same thing, just the name of your template. 

### YOURLANGUAGE 
If an article has multilanguage dimensions, the variable `YOURLANGUAGE` 
will be used to refer to language specific folders. 

For English language only stores, the path 

`/includes/languages/YOURLANGUAGE/`

is just 

`/includes/languages/english/`

### YOURACCOUNT
The variable `YOURACCOUNT` is used to refer to the name of your hosting company
gives to your account.  For cPanel users, this will often be your login username.


### YOURACCOUNTFOLDER 
The variable `YOURACCOUNTFOLDER` is used to refer to the folder in your hosting 
account which holds your site's files.  A very common setup is the following,
assuming the value of `YOURACCOUNT` is `johndoe` (i.e. that your account name is `johndoe`): 

* YOURACCOUNTFOLDER is `/home/johndoe/` - the top level directory you can access using FTP.  Putting files here will mean they are out of reach of a web browser, which can be useful for security;  see [relocating your download folder](/user/security/relocate_download_folder/) for an example.  
* Your Webroot is `/home/johndoe/public_html/` - the top level directory your webserver can access.

Everything will be under `YOURACCOUNTFOLDER` when you view files, either in an [FTP tool](/user/first_steps/useful_tools/#ftp-tools) or in your cPanel's File Manager.  It's even more convenient to set your FTP to go to your webroot, since this is where you will upload your code file changes.

Once you are familiar with these basic terms, you should learn about 
[overrides](/user/first_steps/overrides/). 

