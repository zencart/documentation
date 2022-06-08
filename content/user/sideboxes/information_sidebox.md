---
title: Information sidebox 
description: Making changes to the Information sidebox 
category: sideboxes
weight: 10
---

{{% content_links %}}

### How do I re-arrange the order of the links in the information sidebox?

1. Create (if you don't already have it) a directory named `includes/modules/sideboxes/YOURTEMPLATE/`

2. Copy the includes/modules/sideboxes/information.php file into your new directory

3. Edit the `if` blocks into the order that you would like them to appear.

For example, if you wished the terms and conditions link to appear first, you would move this entire block of php:

```
  if (DEFINE_CONDITIONS_STATUS <= 1) {
    $information[] = '<a href="' . zen_href_link(FILENAME_CONDITIONS) . '">' . BOX_INFORMATION_CONDITIONS . '</a>';
  }
```

 (taking care not to leave the curly bracket behind) to just below the line that says:
```
  unset ($information);
```

### What determines which links are shown in the Information Sidebox? 
- Most of the pages in this sidebox may have links enabled or disabled using [Admin > Configuration > Define Page Status](/user/admin_pages/configuration/configuration_definepagestatus/)
- The About Us and Brands pages have their links controlled by the [site specific overrides](/user/customizing/site_specific_overrides/) file. 


### How do I add a link to the Information Sidebox? 

This question is answered in the FAQ [Adding a Link to the Information sidebox](/user/sideboxes/add_link_information_sidebox/). 

### What if the link should only be available to logged in users? 

Wrap the code that creates the link in a check for the appropriate conditions.  See [protecting pages](/user/customizing/protecting_pages/) for more information. 

