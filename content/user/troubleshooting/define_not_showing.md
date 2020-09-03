---
title: Why does my define page not show up in Define Pages Editor? 
description: I can't see my custom define page in admin 
category: troubleshooting 
weight: 10
---

Define pages are [overridable files](/user/template/template_overrides/), so they can exist in `includes/languages/english/html_includes` and/or in `includes/languages/english/html_includes/YOURTEMPLATE/`. 

However, the [Define Pages Editor](/user/admin_pages/tools/define_pages/) has a quirk: a define file *must* exist in `includes/languages/english/html_includes` for it to be visible to the Define Pages Editor.   So if you create a new file and only put it in the `YOURTEMPLATE` subfolder, it will be visible in the storefront but not in the Define Pages Editor.  Simply copy it to the level above, so that is is in `includes/languages/english/html_includes`, and your problem will be solved. 

