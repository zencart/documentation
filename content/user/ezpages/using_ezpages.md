---
title: Using EZ-Pages 
description: Using EZ-Pages in Zen Cart 
category: ezpages
weight: -1
---

### How do I add text to the EZ-Page Sidebox
To insert the text, we firstly create some over-ride files. If it doesn't already exist, create the following directory  

`includes/templates/YOURTEMPLATE/sideboxes  `

and copy `includes/templates/template_default/sideboxes/tpl_ezpages.php`  
into it. Similarly, if they don't already exist, create an  

`includes/languages/YOURLANGUAGE/extra_definitions/YOURTEMPLATE ` 

directory for each language you are using and copy 
`includes/languages/YOURLANGUAGE/extra_definitions/ez_pages_definitions.php`
 into them.  

Now let's create the text for insertion. Open each of the `ez_pages_definitions.php` files that you just created and insert the following define statement in the appropriate language  

`define('BOX_TEXT_EZPAGES', 'The text you want to insert into your EZ-Pages sidebox');`

This doesn't have to be plain text. If you wish, it can be any string of HTML.  

Next we tell the EZ-Page sidebox to use the text. Open the copy that you made of `tpl_ezpages.php` and insert the line marked below

```
 $content = "";  
 $content .= '<div id="' . str_replace('_', '-', $box_id . 'Content') . '" class="sideBoxContent">';  
 $content .= BOX_TEXT_EZPAGES;  <font color="#ff0000"><----- this is the line that you insert</font>  
 $content  .= "\n" . '<ul style="margin: 0; padding: 0; list-style-type: none;">' . "\n";
```

Finally, upload the new files to your server and check the results in your browser.

### How can I create a link to an EZ-Page? 
For simple menus made up of EZ-Pages and non-EZ-Pages, the best solution is often to use the internal and external link functions within EZ-Pages to bring all of the links into your EZ-Pages' menus. However, sometimes this is not sufficient. An example might be if you only wanted the EZ-Page to be shown when certain conditions were met.

To program an EZ-Page link we can make use of the `zen_ez_pages_link()` function that is built into Zen Cart. This will compile and return the <a> tag with the EZ-Page's information. First you will need to know the EZ-Page ID and chapter number of the page to which you want the link to point. You can find this information by going to Admin > Tools > EZ-Pages. You will find the ID in the left hand column and the chapter number in a column over towards the right of the page.

Armed with this information you can now construct a link based on the following code model.

```
<?php echo zen_ez_pages_link(page ID, chapter number, page is SSL [true/false], 
  open new window [true/false], return full url [true/false]); ?>
```

You must enter a valid page ID as the first parameter. The other parameters are optional and default to 0 for chapter and false for the others. (Hint: Usually you will set the last three parameters to false, false and true respectively.)

### How do I turn off the EZ-Pages Header Bar?

There are two ways to turn off the EZ-Pages header bar. Firstly, it won't show if there are no links there, so turning off all link in the header (Admin > Tools > EZ-Pages) would also suppress display of the bar itself.

Even quicker would be to go to Admin > Configuration > EZ-Pages Settings and set the value of "EZ-Pages Display Status - HeaderBar" to zero.


<!-- please keep this at the end --> 
### I have another EZ-Page question! 
For more complex EZ-Page questions, please post to the 
[main support forum](https://www.zen-cart.com/forum.php).
Please include which version of Zen Cart, and a link to your site URL.
