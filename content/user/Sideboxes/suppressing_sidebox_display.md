---
title: Suppressing sidebox display on specific pages 
category: sideboxes
weight: 1
---

Example application: I want to display some of my sideboxes on my front page only, and suppress them from all other pages.

Let's use the featured product sidebox as an example.  

Create an over-ride for the sidebox's module file. For the featured products sidebox, this would involve copying includes/modules/sideboxes/featured_products.php to includes/modules/sideboxes/YOURTEMPLATE/featured_products.php.  

Open up your new sidebox module file and take a look at the code. 
Generally it will look something like this  

```
<?php  

BIG COMMENT BLOCK  

// test if box should display  
  $show_featured= true;  

  if ($show_featured == true) {  

    // MAIN PROCESSING BLOCK  

  }  
?>
```

All we need to do is to change the line that reads  

```
$show_featured= true;
```

into  

```
  if ($this_is_home_page) {  
    $show_featured = true;  
  } else {  
    $show_featured = false;  
  }
```

If your sidebox module doesn't have a conditional such as 
`if ($show_featured == true) { ... } ` wrapped around the code, then just add it (changing the variable name to something suitable and unique for your sidebox to avoid unintentionally turning off other sideboxes).


