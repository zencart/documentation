---
title: Overrides
description: Zen Cart Template Overrides
category: new_user_topics
weight: 10
---
This article is based on material originally posted by Networkdad, DrByte and other contributors.  

"Template Override" and "Override System" are terms used to describe the collection of files needed to create your own template to customize the look of your cart. Using Overrides allows you to make and save changes to your cart without the fear of losing them when upgrades and patches are released. Also See: [The Override System Simplified](/user/template/template_overrides_simplified/).

**The Override System includes:**  

> Language Files: includes/languages  
>     Module Files: includes/modules  
>     Template Files: includes/templates/template_default  
>     Extra Definitions: includes/languages/YOURLANGUAGE/extra_definitions  
>     Extra Data Files: includes/extra_datafiles


**NOTE:** See [Basic Terms](/user/first_steps/basic_terms/) for an 
explanation of `YOURLANGUAGE` and `YOURTEMPLATE` if these terms are 
unfamiliar. 

**Note:** be sure to read [How do I create a new template?](/user/template/creating_template/)

Remember only files which have been modified should be copied to your /YOURTEMPLATE directory. If you do not make modifications, then by default, Zen Cart® will use the default file.  

**Language Files**  

*   Global information: **/includes/languages/english.php**

> Suppose you want to change the Heading of your Categories sidebox.  
>     Create a new directory: **/includes/languages/YOURTEMPLATE**  
>     Copy <font color="#0000ff">english.php</font> to this new directory  
>     You now have **/includes/languages/YOURTEMPLATE/english.php**  
>     Open the file in a text editor find and modify the following line of code  

```
define('BOX_HEADING_CATEGORIES', 'Categories');
```
>     Save the file and upload your new directory and its contents to your server.

*   Page Specific information: **/includes/languages/YOURLANGUAGE/*.php** (all files within this directory)

> You need to modify some text in account.php - Let's say you want to change every instance of the word 'Account' to     'Profile'  
>     Create a new directory: **/includes/languages/YOURLANGUAGE/YOURTEMPLATE**  
>     Copy <font color="#0000ff">account.php</font> to this new directory  
>     You now have **/includes/languages/YOURLANGUAGE/YOURTEMPLATE/account.php**  
>     Open the file in a text editor find and modify the following line of code  
```
define('MY_ACCOUNT_TITLE', 'My Account');
```

>     Save the file and upload your new directory and its contents to your server.

**Module Files**  

*   Sideboxes information: **/includes/modules/sideboxes/*.php**

> You need to modify sidebox information.php to include another link.  
>     Create a new directory: **/includes/modules/sideboxes/YOURTEMPLATE**  
>     Copy <font color="#0000ff">information.php</font> to this new folder  
>     You now have **/includes/modules/sideboxes/YOURTEMPLATE/information.php**  
>     Open the file in a text editor and modify it to suit your needs  
>     Save the file and upload your new directory and its contents to your server.

**Template Files**  

*   Page templates: `includes/templates/template_default/templates/tpl_XXX_default.php`

> You need to modify some part of  tpl_account_default.php  
>     You should already have the following folder structure **/includes/templates/YOURTEMPLATE/templates**.  
>     Copy <font color="#0000ff">tpl_account_default.php</font> to this directory.  
>     Open the file in a text editor find modify it to suit your needs  
>     Save the file and upload it to your server.

*   Sidebox templates: `**/includes/templates/sideboxes/tpl_***.php**`

> To modify these files follow the steps above, with the exception of the sidebox path.

**Create Your Own Definitions**  

> As you build your template, you may find that you need to include additional definitions.  
>     You can do this by using your text editor to create a definition file - `yourdefinition.php`.
>     All the definitions you need for your template and customization would be included in this file.  
>     Save the file to **includes/languages/YOURLANGUAGE/extra_definitions/yourdefinition.php** and upload it to your server

**Note:** files in this directory get loaded automatically, ensuring your YOURTEMPLATE definitions can be used throughout your cart.  

**Extra Data Files**  

*   YOURTEMPLATE file names - **/includes/filenames.php**

You've created a YOURTEMPLATE page (about_us) and need to reference the filename.  
Create a new file (about_us_filenames.php) which would include the following:  

```
<?php  
// About Us Filename Define  
define('FILENAME_ABOUT_US', 'about_us');  
?>
```

Save the file to **/includes/extra_datafiles/about_us_filenames.php** and upload it to your server.

**Note:** These files will be called automatically, as would any other file in this directory, thereby telling the system what your YOURTEMPLATE filenames are.  

**YOURTEMPLATE Database Tables**  

> You've created a new database field for your UPS tracking system, ups_track and need to define the table name for your code.  
>     Create a new file (ups_track_database_tables.php) which would include the following:  

```
<?php  
// UPS Tracking Table  
define ('TABLE_UPS_TRACK', 'ups_track');  
?>
```

> Save the file to /includes/extra_datafiles/usps_track_database_tables.php and upload it to your server.

**Note:** These files will be called automatically, as would any other file in this directory, thereby telling the system what your YOURTEMPLATE filenames are.  

Extra Javascript for an existing file

> You need to load some javascript for your bizrate account, so that it loads from the existing page (checkout_success.php) after the order has completed.  
>     Create a new file named jscript_bizrate.js which would include the following:  

```
<script language="javascript" type="text/javascript">
 whatever the heck bizrate gave you  
</script>
```

 Save the file to /includes/modules/pages/checkout_success and upload it to your server.

**Zen Cart® Upgrades**  

Using the override system means you don't have to worry about over-writing your YOURTEMPLATE files when an upgrade comes along, because they are all in YOURTEMPLATE directories.  

During an upgrade you may find that new code was added to some of the core files that you are overriding. Its very easy to  compare the files in your override directories to the upgraded files. Using a file compare utility such as Beyond Compare or [WinMerge](http://winmerge.sf.net) you can incorporate the changes into your override files.  

Save the changed files and upload them to your server.
