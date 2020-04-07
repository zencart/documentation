---
title: Template Default - what is it? 
description: Zen Cart Template Default - what is it? 
category: template
weight: 10
---

`template_default` is the master set of template files. Don't touch these (except when doing an upgrade).

Sometimes the word `default` is also used to refer to a 
[default code file](/user/new_user_topics/no_such_file/#how-do-you-find-the-default-file) - a file that can be 
overridden using [template overrides](/user/new_user_topics/overrides/).

Zen Cart also comes with two [other templates](/user/template/other_templates): 
`responsive_classic` and `classic`. 

See the other FAQ on [template overrides](/user/template/template_overrides) for more information.

{{< templates >}}

### Can I use template_default? 

You *do* use the default template in every case where you don't [override](/user/first_steps/overrides/) a file. 

However, you likely don't want to run your store with 
[Tools > Template Selection](/user/admin_pages/tools/template_selection/) 
set to use `template_default`.  The reason for this is that 
the CSS for the default template is specifically designed to make it easy to find the components of a page, rather than for attractive appearance. 
(The question "why is the default template so ugly?" misses this point - 
the CSS for the default template is designed as a pedagogic tool for helping
people learn how to build a template and write CSS.) 

### Is template_default a good base for my new template design? 

The default template was created in an era prior to the widespread use of 
mobile devices.  For this reason, `responsive_classic` is a better choice 
for a base for a new template. 

