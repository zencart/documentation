---
title: Overrides for New Users
description: Template Overrides for New Users
category: new_user_topics
weight: 10
---

This article assumes you are familiar with 
[basic terms](/user/first_steps/basic_terms/) and [template default and default files](/user/first_steps/overrides/). 

"Template Override" and "Override System" are terms used to describe the collection of files needed to create your own template to customize the look of your cart. Using Overrides allows you to make and save changes to your cart without the fear of losing them when upgrades and patches are released. 

**The Override System includes:**  

> Language Files: includes/languages  
> Module Files: includes/modules  
> Template Files: includes/templates/template_default  
> Extra Definitions: includes/languages/YOURLANGUAGE/extra_definitions  
> Extra Data Files: includes/extra_datafiles


**NOTE:** See [Basic Terms](/user/first_steps/basic_terms/) for an 
explanation of `YOURLANGUAGE` and `YOURTEMPLATE` if these terms are 
unfamiliar. 


Remember only files which have been modified should be copied to your /YOURTEMPLATE directory. If you do not make modifications, then by Zen Cart will use the [default file](/user/first_steps/overrides/#default-files).  

**Main Language File**  

*   Default File: `/includes/languages/english.php`

Suppose you want to change the Heading of your Categories sidebox.  
Here are the steps: 

- Create a new directory `/includes/languages/YOURTEMPLATE/`
- Copy `includes/languages/english.php` to this new directory  
- You now have `includes/languages/YOURTEMPLATE/english.php`
- Open the file in a text editor, and find and modify the following line of code  

```
define('BOX_HEADING_CATEGORIES', 'Categories');
```

Save the file and upload your new directory and its contents to your server.

**Page Specific Language File** 

Let's assume you want to change the heading on this page from "My Account Information" to just "My Account". 

- Default File: `/includes/languages/english/account.php`

Here are the steps: 

- Create a new directory `/includes/languages/english/YOURTEMPLATE/` if it doesn't exist 
- Copy `includes/languages/english/account.php` to this new directory  
- You now have `includes/languages/english/YOURTEMPLATE/account.php`
- Open the file in a text editor, and find and modify the following line of code  

```
define('HEADING_TITLE', 'My Account Information');
```

Save the file and upload it to your server.
(If the folder is new, just upload the folder, which will do 
the folder and all files inside it .) 

**Module File**  

Suppose you want to add a link to the Information Sidebox. 

- Default File: `includes/modules/sideboxes/information.php`

Here are the steps: 

- Create a new directory `/includes/modules/sideboxes/YOURTEMPLATE/` if it doesn't exist 
- Copy `includes/modules/sideboxes/information.php` to this new directory  
- You now have `includes/modules/sideboxes/YOURTEMPLATE/information.php`
- Open the file in a text editor, and add a line to the information array.  We won't use language constants for clarity: 

```
$information[] = '<a href="' . zen_href_link(FILENAME_EZPAGES, "id=27") . '">' . "My New EZ-Page". '</a>';
```

**Template File**  

Suppose you want to add a link to the Shopping Cart Page 

- Default File: `includes/templates/template_default/templates/tpl_shopping_cart_default.php` 

Here are the steps: 

- Presumably the directory `/includes/templates/YOURTEMPLATE/templates` exists, but if it doesn't, create it. 
- Copy `includes/templates/template_default/templates/tpl_shopping_cart_default.php` to this new directory  
- You now have `includes/templates/YOURTEMPLATE/templates/tpl_shopping_cart_default.php`
- Open the file in a text editor, and below the `bof shopping cart buttons`, add the line 

```
echo '<a href="' . zen_href_link(FILENAME_EZPAGES, "id=27") . '">' . "My New EZ-Page". '</a>';
```

**Zen Cart Upgrades**  

Using the override system means you don't have to worry about overwriting your YOURTEMPLATE files when an upgrade comes along, because they are all in YOURTEMPLATE directories.  

During an upgrade you may find that new code was added to some of the core files that you are overriding. Its very easy to  compare the files in your override directories to the upgraded files. Using a 
[file compare utility](/user/first_steps/useful_tools/#file-comparison-utility),
you can incorporate the changes into your override files.  

Save the changed files and upload them to your server.

--- 
### Next Steps
Ready to read more about overrides? [Go here](/user/template/template_overrides/).

Or get started [creating your new template](/user/template/creating_template/).
