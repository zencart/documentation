---
title: More Information sidebox 
description: Making changes to the More Information sidebox 
category: sideboxes
weight: 10
---

{{% content_links %}}

 ### How do I remove "Page 1", "Page 2" and "Page 3" from my More Information sidebox?
 Go to Admin > Configuration > Define Page Settings and set their values to 2 or 3.


### How do I add a link to the More Information Sidebox? 

We create the [override file](/user/first_steps/overrides/) `includes/templates/YOURTEMPLATE/sideboxes/tpl_more_information.php`.  Right before the list end 

```
  $content  .= '</ul>' . "\n";
```

we add the link: 

```
    $content .= '<li><a href="https://www.zen-cart.com/" target="_blank" rel="noreferrer noopener">The Greatest Shopping Cart Ever!</a></li>' . "\n" ;
```
