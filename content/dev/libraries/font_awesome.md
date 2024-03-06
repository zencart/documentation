---
title: Font Awesome in Zen Cart 
description: Developer information on the use of fontawesome.io 
category: libraries
weight: 10
type: codepage
---

The [Font Awesome library](https://fontawesome.com/) provides a set of vector icons and social logos for your website.   It is one of the most popular icon sets available. See [Font Awesome](/user/template/fontawesome/) for storeowner docs.

## Font Awesome Versions in Zen Cart 
Both the admin and provided storefront templates (`template_default` and `responsive_classic`) use the same version.

- Font Awesome 6.4 is included in Zen Cart 2.0.0 and above.  
- Font Awesome 4.7 is included in Zen Cart 1.5.5-1.5.8.

## Font Awesome Versions in the Bootstrap Template 

The [Bootstrap template](/user/template/bootstrap/) uses its own version of Font Awesome, which may not be the same as the version used by `template_default`.

- Bootstrap template version 3.5.0 and above uses Font Awesome 5.15. 

## Font Awesome Help and Icons 
Help|Icons
----|----
[Font Awesome 6 Help](https://fontawesome.com/v6/docs) | [Font Awesome 6 icons](https://fontawesome.com/v6/search)
[Font Awesome 5 Help](https://fontawesome.com/v5/docs) |[Font Awesome 5 icons](https://fontawesome.com/v5/search)
[Font Awesome 4.7 Help](https://fontawesome.com/v4.7.0/)|[Font Awesome 4.7 icons](https://fontawesome.com/v4/icons/)

## Backwards Compatibility 

In Zen Cart 2.0.0 and above, for backwards compatibility with plugins that have not yet been updated, by default, the [Font Awesome v4 shim](https://fontawesome.com/v5/docs/web/setup/upgrade-from-v4) is loaded so that older Font Awesome classes may be used.  Loading the shim can be switched off in the [site specific overrides](/user/admin/site_specific_overrides/).

An example of the kind of change that needs to be made to older code to go from V4 to V6 is shown in this image: 

![Font Awesome Migration](/images/fa_6.png)

