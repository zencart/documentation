---
title: Building a Form 
description: Adding a custom form to collect other data
category: code
weight: 10
---

Adding a custom form to your site is a common customization.  There are a 
few guidelines for when you do this: 

- Always [submit your form data using POST](/dev/plugins/upgrading_to_1.5/#rewriting-addon-admin-pages-to-use-form-posts-instead-of-gets). Never use GET for forms. 
- Use `zen_draw_form`, not the HTML `<form>` tag.  Note that when you use `zen_draw_form`, you get the `securityToken` with no extra work. 
- Sanitize your inputs.  

A good model for all of this is the Ask a Question feature, which has been part of Zen Cart since 1.5.7.  See the following files: 

- `includes/modules/pages/ask_a_question/header_php.php`
- `includes/templates/template_default/templates/tpl_ask_a_question_default.php`

