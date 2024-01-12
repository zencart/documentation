---
title: Adding a Link to the Information sidebox 
description: Adding your own links 
category: sideboxes
weight: 10
---

This page continues the FAQ on [customizing the Information Sidebox](/user/sideboxes/information_sidebox/). It is such a common question is has been pulled out to its own page.

The same technique can be used to add a link to the [More Information sidebox](/user/sideboxes/more_information_sidebox/) or the [EZ Page sidebox](/user/sideboxes/ezpages_sidebox/) just by changing the file being edited. 

To add a link to the Information Sidebox, we create the [override file](/user/first_steps/overrides/) `includes/templates/YOURTEMPLATE/sideboxes/tpl_information.php`.  

Edit this file. 

Add your link before the list's ending `ul` tag:

```
$content  .= '</ul>' . "\n";
```

For example, linking to an external page: 

```
$content .= '<li><a href="https://www.zen-cart.com/" target="_blank" rel="noreferrer noopener">The Greatest Shopping Cart Ever!</a></li>' . "\n" ;
```

**Note:** In subsequent examples, the appended linefeed `. "\n"` is dropped for clarity. 

If the link if to an internal page, use the `zen_href_link` function.  For example, if you have a page called "News" (and have defined `FILENAME_NEWS` and `BOX_INFORMATION_NEWS`), a link to this page may be added to the Information Sidebox with 

```
$content .= '<li><a href="' . zen_href_link(FILENAME_NEWS) . '">' . BOX_INFORMATION_NEWS . '</a></li>';
```

If the link is to an internal EZ-Page, use 

```
$content .= '<li><a href="' . zen_href_link(FILENAME_EZPAGES,'id=9') . '">' . "My new page" . '</a></li>';
```

or if you don't want to modify code, you can just use the [EZ-Pages sidebox](/user/sideboxes/ezpages_sidebox/), which displays EZ-Pages with sidebox display on and a positive sort order.  

### Alternate Approaches 

Purists would argue that it's not a good practice to update the template to add links, and that instead, the relevant module file should be updated. (The approach used above is more beginner friendly and lends itself to copy-and-paste ready examples for all three sideboxes, which is why it was chosen.) 

You could accomplish what's done in the first example - add a link to zen-cart.com to the Information sidebox - by creating the 
[override file](/user/first_steps/overrides/) `includes/modules/sideboxes/YOURTEMPLATE/information.php`, and then modifying it just before the `require` statements to add  

```
$information[] = '<a href="https://www.zen-cart.com/" target="_blank" rel="noreferrer noopener">The Greatest Shopping Cart Ever!</a>'; 
```

The same process could be used to add a link to the More Information sidebox, using the `$more_information` array in place of `$information`. 

However, adding a link to the EZ Pages sidebox using this technique would be more involved, since the entries in `$var_linksList` are arrays, not simple strings.

### Specification of URLs 
It's a good practice not to hardcode non-relative URLs, in case your site moves or you want to reconstruct a test instance of it.  So don't do this: 

```
$content .= '<li><a href="https://YOURSTORE.com/index.php?main_page=page&id=25">Important information</a></li>'; // NO 
```

Instead, use an URL relative to the top of your store (or better yet, use `zen_href_link` as in the examples above): 
```
$content .= '<li><a href="index.php?main_page=page&id=25">Important information</a></li>'; // Better
```

You can read more about [the importance of relative URLs](/user/first_steps/relative_urls/) to explore this topic in greater depth. 


### Mobile

You may need to make [additional edits to control the link on mobile displays](/user/template/sideboxes/#controlling-sideboxes-on-mobile-menu).

### More Examples 
See [creating links to other pages](/user/customizing/creating_links/). 
