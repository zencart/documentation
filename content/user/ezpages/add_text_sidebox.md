---
title: How do I add text to the EZ-Page Sidebox? 
description: Adding text to the Important Links sidebox 
category: ezpages
weight: 10
---

To insert the text, we firstly create some override files. If it doesn't already exist, create the following directory  

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


