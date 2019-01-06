# New Templating Features in v2

## shared folder
Zen Cart v2 adds a middle-tier to the template structure, to allow for "shared" customizations which might apply to multiple templates.  These folders are available everywhere the "classic" folder exists (showing a templatable directory).  So for example, if you create `includes/languages/english/html_includes/shared/define_main_page.php`, then any template you install will use this content for the main page; you don't need to replicate this file to `includes/languages/english/html_includes/<new_template>/define_main_page.php` when you create a new template. 


## Product Stock Indicators
Product-stock "availability" and product-"condition" indicators are now available.  

## Product microdata markup
Product microdata markup is provided for search engines to use. 

## Locale.php file 
Language files simplified to relocate locale-specific content into a new locale.php file.  Such things as date format, weight units and are now specified in `includes/languages/english/locale.php`.  This file can be added to a template folder or to the 'shared' folder.

