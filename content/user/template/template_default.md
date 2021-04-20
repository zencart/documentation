---
title: Template Default - what is it? 
description: What is the default template? 
category: template
weight: 10
---

`template_default` is the master set of template files. Don't touch these (except when doing an upgrade).

Sometimes the word `default` is also used to refer to a 
[default code file](/user/new_user_topics/no_such_file/#how-do-you-find-the-default-file) - a file that can be 
overridden using [template overrides](/user/new_user_topics/overrides/).

Zen Cart also comes with another [template](/user/template/other_templates/), called `responsive_classic`. 

See the other FAQ on [template overrides](/user/template/template_overrides/) for more information.

{{< templates >}}

### Can I use template_default? 

You *do* use the it in every case where you don't [override](/user/first_steps/overrides/) a file. 

However, by default, the 
[selected template](/user/admin_pages/tools/template_selection/)
for your store is `responsive_classic`.  

This means that when Zen Cart looks for a template file, a language file, a stylesheet or any other [template file](/user/new_user_topics/template_files/), it looks in `responsive_classic` first.
Then, if the file isn't found, it looks in `template_default`. 

### Is template_default a good base for my new template design? 

Not really.  It was created in an era prior to the widespread use of 
mobile devices.  For this reason, `responsive_classic` is a better choice 
for a base for a new template. 


