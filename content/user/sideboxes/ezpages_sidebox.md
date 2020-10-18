---
title: EZ-Pages sidebox 
description: Customizing the Important Links sidebox  
category: sideboxes
weight: 10
---

{{% content_links %}}

### What controls which links are shown in the EZ-Pages sidebox? 

To get a link to a specific page into the this sidebox, go to [Tools > EZ-Pages](/user/admin_pages/tools/ezpages/), and edit the page you want to add.  Look at the settings for **Sidebox** (between **Header** and **Footer**). 

For the page to show up in the EZ-Pages sidebox, the Sidebox radio button must be set to *Yes* and the sort order must be greater than 0.

![EZ-Pages Sidebox on](/images/ezpages_sidebox_on.png)

### How do I add a new link to the EZ-Page Sidebox? 

We create the [override file](/user/first_steps/overrides/) `includes/templates/YOURTEMPLATE/sideboxes/tpl_ezpages.php`.  

Then edit this file, and follow the instructions provided in [adding a link to the Information Sidebox](/user/sideboxes/add_link_information_sidebox/). 


### How do I add text to the EZ-Page Sidebox? 

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


