---
title: Responsive Classic and Sideboxes 
description: How sideboxes are used in the responsive classic template 
category: sideboxes
weight: 10
---

The responsive classic template will display the built-in sideboxes in the following situations: 

- display on desktop
- display on tablet in landscape mode 

In other modes (phone in portrait or landscape mode, tablet in portrait mode), the built-in sideboxes do not display. 

This behavior is implemented in the several files, so if you want to implement it for *your custom* sideboxes, you'll need to make the changes described below. We'll use the [MailChimp Sidebox](https://www.zen-cart.com/downloads.php?do=file&id=425) as the example. 


a) Edit `includes/templates/responsive_classic/css/responsive_default.css`.  Both the landscape and portrait mode blocks of the CSS turn off the built in sideboxes like this: 

```
div#documentcategories {display:none;visibility:hidden;}
```

This is only done for built-in sideboxes.  To turn off a custom sidebox, you have to add to the CSS.  For the MailChimp sidebox, it would be: 

```
div#mailchimpsidebox {display:none;visibility:hidden;}
```

to both the landscape and portrait blocks of the CSS, below where `documentcategories` is set.

b) Make the same change in `includes/templates/responsive_classic/css/responsive_tablet.css`.

c) Edit `includes/templates/responsive_classic/jscript/jscript_responsive_framework.php`.  Look for `documentcategories` and copy that line, replacing `documentcategories` with `mailchimpsidebox`.

