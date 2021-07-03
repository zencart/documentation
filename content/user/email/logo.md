---
title: Logos in HTML emails 
description: How do I change the logo in my Zen Cart HTML emails ?
category: email
weight: 10
---


The email logo is contained in the file `email/header.jpg`. 

Replace this file with your logo, then update the following two files: 

* `includes/languages/english/YOURTEMPLATE/email_extras.php` 
* `admin/includes/languages/english/email_extras.php`. 

In each file, you will want to update the block 

```
  define ('EMAIL_LOGO_FILENAME', 'header.jpg');  //-File is present in /email folder
  define ('EMAIL_LOGO_WIDTH', '550');
  define ('EMAIL_LOGO_HEIGHT', '110');
  define ('EMAIL_LOGO_ALT_TITLE_TEXT', 'Zen Cart! The Art of E-commerce');
```

If you use the same logo for your site and your email, the values for these defined constants will be the same ones as you entered in your `includes/languages/english/YOURTEMPLATE/header.php` file. 

Sometimes the change will not show up right away in emails that have already been sent and viewed, due to caching. Simply close your email program and re-open it to see the change take effect.  If your email is browser-based, clear your browser cache to see the change.  See [caching](/user/new_user_topics/browser_caching/) for more details. 

**NOTE: You must be sending HTML emails for this to work.**  See the Enable HTML Emails setting in [Admin > Configuration > Email Options ](/user/admin_pages/configuration/configuration_emailoptions/) setting.

## Related Articles 
- [Using your logo on packing slips and invoices](/user/orders/high_res_logo)
- [Changing the logo in the header](/user/new_user_topics/change_header_logo/)
