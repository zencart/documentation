---
title: Language Files - What are they and how are they used? (1.5.7-)
description: How do I change language text in 1.5.7 or below? 
category: new_user_topics
weight: 10
---

**NOTE:** These instructions are for Zen Cart 1.5.7 and below. If you need instructions for 1.5.8 or above, please see [Language Files - 1.5.8](/user/new_user_topics/language_files/). 

Zen Cart uses language files or a "languages system"  to define the text content used by the various display pages of your cart.  

An obvious benefit of the "languages system" is the ability to run Zen Cart in another language or several languages at the same time. Using these files allows you to edit/change the content that appears on every page of your shop without needing to understand databases or programming languages.  

The information in these files can be placed into four categories as follows:  

**Global information** which contains text that is used across the entire site. This information is contained in `includes/languages/english.php`.  

**Page Specific information** contains text used by individual pages in your cart. This information is contained in `includes/languages/english/PAGENAME.php`. 

**Your Own Definitions** can contain text you might find necessary in your particular shop. This information is contained in `.php` files stored in the folder 
`include/languages/english/extra_definitions/`.

**Define pages** are default pages used by Zen Cart and can be edited as necessary. You can also add your own pages if you find that necessary. These files are located in `includes/languages/english/html_includes/`.  For more information on this topic, see [setting up Define Pages](/user/new_user_topics/setting_up_define_pages). 

The information in language files (other than the define pages described above) is constructed using PHP "define statements," which consist of a CONSTANT and the information contained in that CONSTANT as shown in the example below.  

```
define('MY_CONSTANT', 'This is my information');
```

The advantage of these "define statements" is that text information can be included in your template files using a constant rather than a hardcoded value, 
allowing you to easily change templates but preserve your language customizations.  It also facilitates [making your store multi-language](/user/localization/languages/).

## **Examples and Usage**

> **Global Definitions**

> The definitions in `includes/languages/english.php` include the footer text, the sidebox headings, text used by the forms in Zen Cart and various error messages.  
> 
> *   From `includes/languages/english.php`

```
define('BOX_HEADING_CATEGORIES', 'Categories');
...
define('ENTRY_FIRST_NAME', 'First Name:');
... 
define('ENTRY_STREET_ADDRESS_ERROR', 'Your Street Address must contain a minimum of ' . ENTRY_STREET_ADDRESS_MIN_LENGTH . ' characters.');
```

> **Page Specific Definitions**  
> These definitions are exactly what the title says; They define text information for specific display pages in your cart.  
> The basic information in these files includes the text for the page heading and the text for the navbar. Depending on the page, you will also find information for e-mail messages and for the tasks carried out by a particular display page.  

> *   From `includes/languages/english/conditions.php`:

```
define('NAVBAR_TITLE', 'Conditions of Use');
define('HEADING_TITLE', 'Conditions of Use');
```

> *   From `includes/languages/english/header.php`:
```
define('HEADER_ALT_TEXT', 'Powered by Zen Cart :: The Art of E-Commerce');
```

```
define('HEADER_SALES_TEXT', 'TagLine Here');  
define('HEADER_LOGO_WIDTH', '192px');  
define('HEADER_LOGO_HEIGHT', '64px');  
define('HEADER_LOGO_IMAGE', 'logo.gif');</span>
```
> 
> *   From `includes/languages/english/contact_us.php`
```
define('ENTRY_NAME', 'Full Name:');
define('ENTRY_EMAIL', 'Email Address:');
define('ENTRY_ENQUIRY', 'Message:');
```


> **Your Own Definitions**  
> As you customize your cart, you may find that you need to include additional definitions. You can do this by creating a definition file (say, `yourdefinitionfile.php`) and saving it to `includes/languages/ENGLISH/extra_definitions`
Constructing your own defines would follow the pattern shown above.  

> **Define Pages**  
> These pages include your privacy statement, your conditions of use and shipping and handling information.  
> These files can be edited in a text editor and uploaded to your server, or you can edit them in your admin control panel in the [Define Pages Editor](/user/admin_pages/tools/define_pages/). 

> *   Pages from this folder

```
define_privacy.php  
define_conditions.php  
define_shippinginfo.php
```
