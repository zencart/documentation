---
title: Miscellaneous EZ-Pages Questions
category: ezpages
weight: -1
---

{{< misc >}} 

---
### How can I create a link to an EZ-Page? 
For simple menus made up of EZ-Pages and non-EZ-Pages, the best solution is often to use the internal and external link functions within EZ-Pages to bring all of the links into your EZ-Pages' menus. However, sometimes this is not sufficient. An example might be if you only wanted the EZ-Page to be shown when certain conditions were met.

To program an EZ-Page link we can make use of the `zen_ez_pages_link()` function that is built into Zen Cart. This will compile and return the <a> tag with the EZ-Page's information. First you will need to know the EZ-Page ID and chapter number of the page to which you want the link to point. You can find this information by going to Admin > Tools > EZ-Pages. You will find the ID in the left hand column and the chapter number in a column over towards the right of the page.

Armed with this information you can now construct a link based on the following code model.

```
<?php echo zen_ez_pages_link(page ID, chapter number, page is SSL [true/false], 
  open new window [true/false], return full url [true/false]); ?>
```

You must enter a valid page ID as the first parameter. The other parameters are optional and default to 0 for chapter and false for the others. (Hint: Usually you will set the last three parameters to false, false and true respectively.)

---
### How do I turn off the EZ-Pages Header Bar?

There are two ways to turn off the EZ-Pages header bar. Firstly, it won't show if there are no links there, so turning off all link in the header (Admin > Tools > EZ-Pages) would also suppress display of the bar itself.

Even quicker would be to go to Admin > Configuration > EZ-Pages Settings and set the value of "EZ-Pages Display Status - HeaderBar" to zero.

---
### How can I add Meta Tags to my EZ-Pages? 

Use the [EZ-Pages Meta Tag Fields](https://www.zen-cart.com/downloads.php?do=file&id=746) plugin. 

---
### Sorry, the page you were attempting to access cannot be found

**Issue:** When I visit my page, I get the error message, "Sorry, the page you were attempting to access cannot be found." 

This means you have not configured the EZPage correctly.  You need to set 
the radio button to *Yes* and the sort order to a value > 0 for either the
Header, the Sidebox or the Footer.  Alternately, in Zen Cart 1.5.6 and above,
you can set the *Page is Visible* radio button to *Yes*.  See the help for [Tools > EZ-Pages](/user/admin_pages/tools/ezpages/) for more details. 


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
