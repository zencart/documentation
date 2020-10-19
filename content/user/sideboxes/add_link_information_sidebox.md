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

If the link is to an internal page, use the `zen_href_link` function.  For example, the About Us page can be added to the Information Sidebox with 

```
$content .= '<a href="' . zen_href_link(FILENAME_ABOUT_US) . '">' . BOX_INFORMATION_ABOUT_US . '</a>';
```

If the link is to an internal EZ-Page, use 

```
$content .= '<a href="' . zen_href_link(FILENAME_EZPAGES,'id=9') . '">' . "My new page" . '</a>';
```

or you can just display it in the [EZ-Pages sidebox](/user/sideboxes/ezpages_sidebox/). 

It's a good practice not to hardcode non-relative URLs, in case your site moves or you want to reconstruct a test instance of it.  So don't do this: 

```
$content .= '<a href="https://YOURSTORE.com/index.php?main_page=page&id=25">Important information</a>'; // NO 
```

Instead, use an URL relative to the top of your store (or better yet, use `zen_href_link` as in the examples above): 
```
$content .= '<a href="index.php?main_page=page&id=25">Important information</a>'; // Better
```

You can read more about [the importance of relative URLs](/user/first_steps/relative_urls/). 


### Mobile

You may need to make [additional edits to control the link on mobile displays](/user/template/sideboxes/#controlling-sideboxes-on-mobile-menu)
