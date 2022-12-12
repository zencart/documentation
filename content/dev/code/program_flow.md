---
title: Program Flow
description: Execution Path for a Zen Cart Page Visit
category: code
weight: 10
type: codepage
---

A storefront visit in Zen Cart follows an MVC style approach, albeit largely based on procedural code. The files involved are processed roughly in the order shown below. 

## AutoLoading 
At various points there may be [auto-loading](/dev/code/inclusion/) of certain files in a certain directory matching a prescribed naming convention, or all files automatically executed according to certain rules for that location.

If debugging the program flow, there is a useful constant called `DEBUG_AUTOLOAD` which will show the file loading order in the browser output if set to true:
```php
define('DEBUG_AUTOLOAD', false);
```

See [Checking file loading](/user/troubleshooting/blank_page/#6-checking-file-loading) for instructions on use. 

## File Load Order
Locations where an "override" can be used are noted with a ► symbol.

- `/index.php`

- `/includes/application_top`
  - `/includes/local/configure.php`, `/includes/configure.php`
  - `/includes/defined_paths.php`
  - ►`/includes/extra_configures/*.php`

- ►`/includes/autoloaders/config.xxxx.php` files (the [Init System](/dev/code/init_system/)) loads things in the order defined inside the files, which follows essentially the following order:
  - Connect to database and setup caching
  - `/includes/filenames.php`
  - `/includes/database_tables.php`
  - ►`/includes/extra_datafiles/*.php` (usually to load extra db tablenames or custom defines)
  - Read configuration keys from database (as set in Admin)
  - Start gzip compression if enabled
  - Load functions
      - `functions_general` and most other functions files, including `html_output`, `functions_email`, etc.
      - ►`/includes/functions/extra_functions/*.php`
  - Set up and start session if valid
      - Check for cookie support
      - Check to see if the customer is a spider/robot, and act accordingly
      - SSL and IP validation checks
  - Instantiate `shopping_cart` class
  - Sanitize and validate URL parameters
  - Language Selection
  - ►`/includes/languages/LANGUAGE/extra_definitions`
  - Template Selection
  - Setup currencies
  - Enable navigation history
  - Load MessageStack
  - Check for “Down For Maintenance” or “Customer Not Authorized yet” status
    - ►`/includes/init/includes/init_customer_auth.php`
  - Process Cart Content Adds/Update, File Uploads
  - Process specialized functions
      - Who’s online detection and logging
      - Activate and Expire any time-scheduled Banners, Specials, Features, Salemaker, Upcoming Products
  - Calculate category/product path (cPath)
  - Load category-tree class, and prepare the categories-sidebox contents
  - Start the breadcrumb class and add current page components to it
  - Start [observer/notifier](/dev/code/notifiers/) infrastructure
  - Calculate and display any system error messages if relevant

- `/includes/modules/pages/PAGE/header_php►*.php` files:
  - ►loads `/languages/LANGUAGE/TEMPLATE/PAGENAME.php`
  - update the breadcrumbs appropriate for this page
  - (occasionally calls a specific `tpl_xxxx.php` file, although usually things carry on through the following steps first)

- ►`/includes/templates/common/html_header.php`
  - `<HTML><HEAD>`
  - `/includes/modules/meta_tags.php`
  - display canonical metatag links based on language etc
  - ►`/includes/templates/TEMPLATE/CSS/style*.css`
  - load jQuery from jQuery CDN
  - `modules/pages/PAGE/jscript*.js` for static `<script>` snippets
  - `modules/pages/PAGE/jscript*.php` for dynamic or conditional `<script>` code
  - `</HEAD>`
  
- `/includes/templates/common/main_template_vars.php`
  - Prepares the content for the “center” section of the page (doesn’t display until done processing)
  - Content is prepared from either of:
      - `includes/modules/pages/PAGE/main_template_vars.php` (► and any additional files it calls) 
      - ►`includes/templates/TEMPLATE/templates/tpl_PAGE_default.php` (this is usually also called by `main_template_vars.php` from the line above)

- ►`/includes/templates/jscript/on_load/*.js`
  - loads any customized code for the “onload” parameter of the <body> tag which gets output in `tpl_main_page`

- ►`/includes/templates/TEMPLATE/common/tpl_main_page` (The following order is from template_default, as an example; some templates may alter this)
  - `<BODY>`
  - output Banner Area 1
  - ►`/TEMPLATE/common/tpl_header.php`
      - Output Header rows (logo, nav bar, search box, etc)
      - Output Banner Area 2
  - output Left sideboxes  (`/modules/column_left`)
  - output “body content” from `main_template_vars` or `tpl_page_default` above
      - Output Breadcrumbs and  Banner Area 3, and any MessageStack messages
  - output Banner Area 4
  - output Right sideboxes  (`/modules/column_right`)
  - ►`/templates/common/tpl_footer.php`
      - Footer Navigation bar (including ez-pages tagged for footer)
      - Display IP Address
      - utput Banner Area 5
      - ►Display footer text (from language file)
  - Output Banner Area 6
  - `</HTML>`

- `/includes/application_bottom.php`
  - close SESSION, end GZIP compression and dump buffered data to the screen, if applicable.
  
