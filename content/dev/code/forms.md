---
title: Building a Form 
description: Adding a custom form to collect data
category: code
weight: 10
---

Adding a custom form to your site is a common customization.  There are a few guidelines for when you do this: 

- Always [submit your form data using POST](/dev/plugins/upgrading_to_1.5/#rewriting-addon-admin-pages-to-use-form-posts-instead-of-gets). Never use GET for forms. (There are exceptions of course, but if you don't already grok best practices for that, then never use GET for forms!)
- Use `zen_draw_form`, not the HTML `<form>` tag.  Note that when you use `zen_draw_form`, you get the `securityToken` with no extra work. 
- [Sanitize your inputs](/dev/code/database_querying/).

A good model for all of this is the Ask a Question feature, which has been part of Zen Cart since 1.5.7.  See the following files: 

- `includes/modules/pages/ask_a_question/header_php.php`
- `includes/templates/template_default/templates/tpl_ask_a_question_default.php`

### Alternative Approach - Use a Form Builder 

Another option which is highly recommended for storeowners who don't have a developer is to use a form building tool like [Wufoo](https://www.wufoo.com/). 

A Wufoo form can easily be embedded on a extra define page (page_2, page_3, page_4) or an existing page like Contact Us.  In the case of Contact Us, you would just edit the template file (`includes/templates/YOURTEMPLATE/templates/tpl_contact_us_default.php`) and replace the built-in form with the script from Wufoo.  Similarly, using a define page would just mean editing the template file and inserting the script below the `content` div. 

 
