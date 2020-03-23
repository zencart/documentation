---
title: Template Default - what is it? 
category: template
weight: 10
---

`template_default` is the master set of template files. Don't touch these (except when doing an upgrade).

`classic` is a sample custom template. You can create many custom templates. `classic` is just an example. Anything that's not in your custom template but exists in template_default will be automatically loaded from template_default for you. Thus, when you're building a custom template, all you need in your custom template folder is the files/folders that you've customized/changed/added.
If you need to customize the "specials" page for example, you would copy the template_default version of the specials template into your custom template's folders (using same folder structure as template_default), and make your changes to your custom copy. Same with images, stylesheets, buttons, etc. 

`responsive_classic` is another sample custom template which works on mobile devices. 

See the other FAQs on the template system and on overrides for more information.

