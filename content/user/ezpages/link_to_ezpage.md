---
title: How can I create a link to an EZ-Page? 
description: Using the zen_ez_pages_link function 
category: ezpages
weight: 10
---

For simple menus made up of EZ-Pages and non-EZ-Pages, the best solution is often to use the internal and external link functions within EZ-Pages to bring all of the links into your EZ-Pages' menus. However, sometimes this is not sufficient. An example might be if you only wanted the EZ-Page to be shown when certain conditions were met.

To program an EZ-Page link we can make use of the `zen_ez_pages_link()` function that is built into Zen Cart. This will compile and return the <a> tag with the EZ-Page's information. First you will need to know the EZ-Page ID and chapter number of the page to which you want the link to point. You can find this information by going to Admin > Tools > EZ-Pages. You will find the ID in the left hand column and the chapter number in a column over towards the right of the page.

Armed with this information you can now construct a link based on the following code model.

```
<?php echo zen_ez_pages_link(page ID, chapter number, page is SSL [true/false], 
  open new window [true/false], return full url [true/false]); ?>
```

You must enter a valid page ID as the first parameter. The other parameters are optional and default to 0 for chapter and false for the others. (Hint: Usually you will set the last three parameters to false, false and true respectively.)

