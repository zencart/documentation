---
title: Other templates for Zen Cart
description: Changing the appearance of your cart by using a new template
category: template
weight: 10
---

The base template is Zen Cart is called [template_default](/user/template/template_default/). 

Classic is a sample custom template. You can create your own custom templates;  Classic is just an example. Anything that's not in your custom template but exists in template_default will be automatically loaded from template_default for you. Thus, when you're building a custom template, all you need in your custom template folder are the files/folders that you've customized/changed/added. Everything else is taken from the [default files](/user/first_steps/overrides/#default-files). 

Responsive Classic is another sample custom template, but it is more modern than Classic. It was designed [to be responsive](/user/template/responsive/), which is a way of saying that it works on mobile devices.  When the `classic` template was created, there were no mobile devices, so that wasn't a concern.  More details on this template are provided in the [Responsive Classic FAQ](/user/template/responsive_classic/).

The community contributed [bootstrap template](/user/template/bootstrap/) is another good option for a responsive template. 

{{< templates >}}

<br>

See the other FAQs on [the template system and overrides](/user/template/) for more information.


### Commercial Templates 

There are software vendors who sell templates for Zen Cart.  Many of them are extremely visually attractive.  But exercise caution! 

- Some of these templates were built for WordPress, not Zen Cart, so they don't respect configuration settings and are much harder to work on.
- Some of these templates were built under PHP 5.6 and need extensive fixing before they can run error-free under current versions of PHP. 
- Some of these templates were built for much older versions of Zen Cart, and haven't been upgraded.  
- Some of these templates will use PHP short "open" tags, which are deprecated and scheduled for removal from PHP.
- Some of these templates include old versions of JavaScript libraries, which must be updated. 
- Some of these templates remove large pieces of core code functionality to simplify the template builder's job (because they don't take the time to learn all the things Zen Cart can do with its various configuration switches or product features), which means that things you would expect to work do not.
- Some of these templates will not have incorporated the latest [template security changes](/user/template/template_changes/).

Be sure to discuss these issues with your template provider and make the transaction with an awareness of what you are taking on.  
Don't be afraid to get them to put in writing whether they have tested the template's functionality with all of Zen Cart's features, and whether they will support you if things "break" when you change Zen Cart configuration settings.

### Switching templates during an upgrade 

As is noted in the [detailed upgrading guide](/user/upgrading/detailed_upgrading/), an upgrade is not the ideal time to switch templates; consider upgrading first and then choosing a new template. 

> Tweaking templates "to perfection" can endlessly delay implementing an upgrade if you aren't diligent. 

If you *must* change templates (because you're coming from an old version of Zen Cart with a non-responsive template, for example), consider using the [Responsive Classic](/user/template/responsive_classic/) template until your upgrade is complete and live, and *then* changing your template. 


## Accessibility and Templates
Both the 
[Responsive Classic template](/user/template/responsive_classic/) and the 
[Bootstrap template](/user/template/bootstrap/) are not only kept up to date,
but are rated highly by accessibility testers out of the box.  If you use
another template - particularly a commercial template - you will have to 
perform your own [accessibility testing](/user/accessibility/accessibility/) and 
make any necessary adjustments yourself. 


