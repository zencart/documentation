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

If you're running on Zen Cart 2.0.1 or later, refer to [Adding a Link to the Information Sidebox](/user/sideboxes/add_link_information_sidebox/) for a way to add the link via an observer.

Otherwise, we create the [override file](/user/first_steps/overrides/) `includes/templates/YOURTEMPLATE/sideboxes/tpl_more_information.php`, edit this file and follow the instructions provided in [Adding a Link to the Information Sidebox](/user/sideboxes/add_link_information_sidebox/). 
