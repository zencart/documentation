---
title: Dependency Checks
weight: 10
layout: docs
category: release_process
---

Before doing a build (especially a new release vs. a patch), it's a good idea to check and update versions of external utilities that the project uses. 

**Try to do these a few weeks before the build so you have time to test, and you don't break the build at the last minute.**

The following should be checked: 

- `includes/classes/vendors/PHPMailer`
- `includes/classes/Mobile_Detect.php`
- `admin/includes/javascript/jquery-ui-i18n.min.js`

Embedded references to external files that may require updating: 

- jQuery library:
  - `zc_install/includes/template/common/html_header.php`
  - `includes/templates/responsive_classic/common/html_header.php`
  - `includes/templates/template_default/common/html_header.php`
  - `admin/includes/javascript_loader.php`
  - `admin/includes/ckeditor.php`

- jQuery flot library:
   - `admin/banner_manager.php`
   - `admin/banner_statistics.php`
 
- jQuery mmenu: 
  - `includes/templates/responsive_classic/common/html_header.php `
  - `includes/templates/responsive_classic/templates/tpl_modules_mobile_menu.php `

- jQuery UI:
  - `admin/includes/admin_html_head.php`
  - `admin/includes/javascript_loader.php`

- jQuery jAlert: 
   - `admin/includes/keepalive_module.php`

- Bootstrap:
  - `includes/templates/template_default/templates/tpl_zc_phpupgrade_default.php`
  - `includes/templates/template_default/templates/tpl_zc_install_suggested_default.php`
  - `admin/includes/admin_html_head.php`
  - `admin/includes/javascript_loader.php`

- Font Awesome:
  - `includes/templates/responsive_classic/common/html_header.php`
  - `admin/includes/admin_html_head.php`
  - `admin/includes/css/font-awesome.min.css`
  - `admin/includes/stylesheet.css`


