---
title: Logos in HTML emails 
description: How do I change the logo in my Zen Cart HTML emails ?
category: email
weight: 10
---

Related: [Using your logo on packing slips and invoices](/user/customizing/use_company_logo/).

The email logo is contained in the file `email/header.jpg`. 

Replace this file with your logo, then update the files which specify
this filename and the logo's dimensions.  

For admin, this file is `admin/includes/languages/english/email_extras.php`. 
You will want to update the block 

```
  define ('EMAIL_LOGO_FILENAME', 'header.jpg');  //-File is present in /email folder
  define ('EMAIL_LOGO_WIDTH', '550');
  define ('EMAIL_LOGO_HEIGHT', '110');
  define ('EMAIL_LOGO_ALT_TITLE_TEXT', 'Zen Cart! The Art of E-commerce');
```

For the storefront, copy the file `includes/languages/english/email_extras.php` to `includes/languages/english/YOURTEMPLATE/email_extras.php` and update the same block of `define` statements.

Sometimes the change will not show up right away in emails that have already been sent and viewed, due to caching. Simply close your email program and re-open it to see the change take effect.  If your email is browser-based, clear your browser cache to see the change.  See [Image Caching](/user/new_user_topics/change_header_logo/#image-caching) for more details. 

**NOTE: ** You must be sending HTML emails for this to work.**  See the Enable HTML Emails setting in [Admin > Configuration > Email Options ](/user/admin_pages/configuration/configuration_emailoptions/) setting.
