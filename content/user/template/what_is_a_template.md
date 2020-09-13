---
title: What is a Template? 
description: Basic information about about Templates in Zen Cart
category: template
weight: -5
---

Before you read this article, please be sure you are familiar with 
[Basic Terms](/user/first_steps/basic_terms/) used in describing
Zen Cart files. 

---
### What is a template? 
A template (sometimes called a "theme") is a set of files that controls how
the Zen Cart storefront looks.  

The following list outlines the elements of a template: 

- [Template Pages](/user/template/template_pages/) - how content display is structured
- [Sideboxes](/user/template/sideboxes/) - narrow pieces of content that are placed on the left and right edges of all pages
- [Centerboxes](/user/template/centerboxes/) - wide pieces of content that are placed in the center of the page on specific pages 
- [Stylesheet](/user/template/stylesheet/) - the CSS that controls the layout of the site 
- [Responsiveness](/user/template/responsive/) - modern templates must look good on mobile devices like phones and tablets 


### What's the difference between templates and overrides? 
Creating a new template means you are using the 
[overrides](/user/first_steps/overrides/) system, 
even if just to create `includes/templates/YOURTEMPLATE` and 
folders below that.   But generally, a new template also uses 
more overrides: 

- language file overrides like `includes/languages/YOURTEMPLATE` and `includes/languages/english/YOURTEMPLATE` 
- code overrides like `/includes/modules/YOURTEMPLATE`

---
### What can I not override?
See [the list of non-overridable files](/user/template/template_overrides/#what-can-i-not-override).

---
### What is template default? 
See [the template default FAQ](/user/template/template_default/). 

---
### I created a new template, but can't see it in Admin > Tools > Template Selection

This can happen if you have forgotten to create the `template_info.php` file. 
See [the template_info FAQ](/user/template/template_info/). 

