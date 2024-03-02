---
title: Language Files - What are they and how are they used? (1.5.8+)
description: How do I change language text in 1.5.8 and above? 
category: new_user_topics
weight: 10
---

**NOTE:** These instructions are for Zen Cart 1.5.8 and higher. If you need instructions for 1.5.7 or below, please see [Language Files - 1.5.7](/user/new_user_topics/157_language_files/). 

Zen Cart uses language files or a "languages system"  to define the text content used by the various display pages of your cart.  

An obvious benefit of the "languages system" is the ability to run Zen Cart in another language or several languages at the same time. Using these files allows you to edit/change the content that appears on every page of your shop without needing to understand databases or programming languages.  

The information in these files can be placed into four categories as follows:  

**Global information** which contains text that is used across the entire site. This information is contained in `includes/languages/english.php`.  

**Page Specific information** contains text used by individual pages in your cart. This information is contained in `includes/languages/english/PAGENAME.php`. 

**Your Own Definitions** can contain text you might find necessary in your particular shop. This information is contained in `.php` files stored in the folder 
`include/languages/english/extra_definitions/`.

**Define pages** are default pages used by Zen Cart and can be edited as necessary. You can also add your own pages if you find that necessary. These files are located in `includes/languages/english/html_includes/`.  For more information on this topic, see [setting up Define Pages](/user/new_user_topics/setting_up_define_pages). 

The information in language files (other than the define pages described above) is constructed by building a PHP array of definitions.  When all language files have been read, these arrays are built into constant definitions using PHP "define statements." 

In older versions, constants were defined directly in language files; this was changed in Zen Cart 1.5.8 because of new restrictions on the re-definition of constants in PHP 8. 

The advantage of separating out language strings is that text information can be included in your template files using a constant rather than a hardcoded value, 
allowing you to easily change templates but preserve your language customizations.  It also facilitates [making your store multi-language](/user/localization/languages/).

## **Examples and Usage**

> **Global Definitions**

> The definitions in `includes/languages/lang.english.php` include the footer text, the sidebox headings, text used by the forms in Zen Cart and various error messages.  
> 
> *   From `includes/languages/lang.english.php`

```
$define = [
'BOX_HEADING_CATEGORIES' => 'Categories',
...
'ENTRY_FIRST_NAME' => 'First Name:', 
... 
'ENTRY_STREET_ADDRESS_ERROR' => 'Your Street Address must contain a minimum of ' . ENTRY_STREET_ADDRESS_MIN_LENGTH . ' characters.',
```

> **Page Specific Definitions**  
> These definitions are exactly what the title says; They define text information for specific display pages in your cart.  
> The basic information in these files includes the text for the page heading and the text for the navbar. Depending on the page, you will also find information for e-mail messages and for the tasks carried out by a particular display page.  

> *   From `includes/languages/english/lang.conditions.php`

```
$define = [
    'NAVBAR_TITLE' => 'Conditions of Use',
    'HEADING_TITLE' => 'Conditions of Use',
...
```

> *   From `includes/languages/english/lang.header.php`:
```
$define = [
...
    'HEADER_ALT_TEXT' => 'Powered by Zen Cart :: The Art of E-Commerce',
    'HEADER_LOGO_IMAGE' => 'logo.gif',
    'HEADER_LOGO_WIDTH' => '254',
    'HEADER_LOGO_HEIGHT' => '68',
...

```

> 
> *   From `includes/languages/english/lang.contact_us.php`:
```
$define = [
    'HEADING_TITLE' => 'Contact Us',
    'NAVBAR_TITLE' => 'Contact Us',
...
```


> **Your Own Definitions**  
> As you customize your cart, you may find that you need to include additional definitions. 

- You can create a new-style definition file (say, `lang.yourdefinitionfile.php`), and save it to `includes/languages/ENGLISH/extra_definitions`.

- As long as the definitions are not already used in Zen Cart, you may also create an old-style definition file (using the syntax from [Language Files - 1.5.7](/user/new_user_topics/157_language_files/). 


> **Define Pages**  
> These pages include your privacy statement, your conditions of use and shipping and handling information.  
> These files can be edited in a text editor and uploaded to your server, or you can edit them in your admin control panel in the [Define Pages Editor](/user/admin_pages/tools/define_pages/). 

> *   Pages from this folder (partial list)

```
define_privacy.php  
define_conditions.php  
define_shippinginfo.php
```

