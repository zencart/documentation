---
title: How do I change the "Welcome to Zen Cart!" image?
description: Removing or changing the picture from the home page
category: new_user_topics 
weight: 10
---

To remove this image, you want to modify the file `includes/languages/english/html_includes/define_main_page.php`, or the file `includes/languages/english/html_includes/responsive_classic/define_main_page.php` if you are using the responsive classic template.

Open this file, and remove the first line, which displays the image.  You may want  to make additional changes to customize the content for your specific needs. 
Save the edited file to `includes/languages/english/html_includes/YOURTEMPLATE/define_main_page.php` and upload it to your server.

If you are using a language other than English, save the file to `includes/languages/YOURLANGUAGE/html_includes/YOURTEMPLATE/define_main_page.php` and upload it to your server.

**NOTE:** See [Basic Terms](/user/first_steps/basic_terms/) for an 
explanation of `YOURLANGUAGE` and `YOURTEMPLATE` if these terms are 
unfamiliar. 

