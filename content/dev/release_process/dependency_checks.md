---
title: Dependency Checks
weight: 10
layout: docs
category: release_process
---

Before doing a build (especially a new release vs. a patch), it's a good idea to check and update versions of external utilities that the project uses. It's not necessary to be on the latest version, but you want to ensure that any security patches have been installed.  

**Last minute changes are risky!  Try to do any changes a few weeks before the build so you have time to test.**

Also, make time to run a [Lighthouse check](/user/upgrading/javascript_updates/) before the release to be sure no Javascript libraries with known vulnerabilities are in use. 

The following should be checked: 

## Complete Projects 
|Project|File|Project URL|
|-------|----|-----------|
|PHPMailer|`includes/classes/vendors/PHPMailer`|https://github.com/PHPMailer/PHPMailer|
|Mobile Detect|`includes/classes/Mobile_Detect.php`|https://github.com/serbanghita/Mobile-Detect/|
|jQuery|`includes/templates/responsive_classic/jscript/jquery.min.js`<br>`includes/templates/template_default/jscript/jquery.min.js`<br>`admin/includes/javascript/jquery.min.js`|https://jquery.com/|
|jQuery UI|`admin/includes/javascript/jquery-ui-i18n.min.js`|https://jqueryui.com/|
|Font Awesome|`admin/includes/css/font-awesome.min.css`|https://fontawesome.com/|
|Bootstrap|`admin/includes/css/bootstrap.min.css`|https://getbootstrap.com/|
|YAML|`zc_install/includes/vendors/yaml`|https://yaml.org/|
|Laravel|`laravel/vendor/*`|https://laravel.com/|

## References within Files 

Embedded references to external files that may require updating: 

- jQuery library: https://jquery.com/ 
  - `zc_install/includes/template/common/html_header.php`
  - `includes/templates/responsive_classic/common/html_header.php`
  - `includes/templates/template_default/common/html_header.php`
  - `admin/includes/javascript_loader.php`
  - `admin/includes/ckeditor.php`

- jQuery flot library: https://github.com/flot/flot
   - `admin/banner_manager.php`
   - `admin/banner_statistics.php`
 
- jQuery mmenu: https://plugins.jquery.com/mmenu/
  - `includes/templates/responsive_classic/common/html_header.php `
  - `includes/templates/responsive_classic/templates/tpl_modules_mobile_menu.php `
 
Note that the license for mmenu changed in their v5.6.0 to CC-BY-NC-4.0, which is not compatible with Zen Cart's GPLv2 license. So cannot distribute 5.6.0 or newer with Zen Cart. Bugfixes must be applied directly to current distro files instead.

- jQuery UI: https://jqueryui.com/ 
  - `admin/includes/admin_html_head.php`
  - `admin/includes/javascript_loader.php`

- jQuery jAlert: https://github.com/HTMLGuyLLC/jAlert 
   - `admin/includes/keepalive_module.php`

- jQuery jTimeout: https://github.com/HTMLGuyLLC/jTimeout 
   - `admin/includes/keepalive_module.php`

- Bootstrap: https://getbootstrap.com/
  - `admin/includes/admin_html_head.php`
  - `admin/includes/javascript_loader.php`

 Note that the following error-condition template files do not share common header components from the default template because they are intended to be as "standalone" as possible, in case other template-system files are damaged:
  - `includes/templates/template_default/templates/tpl_zc_phpupgrade_default.php`
  - `includes/templates/template_default/templates/tpl_zc_install_suggested_default.php`

> CAUTION: Be mindful that upgrading Bootstrap between Bootstrap's "major" releases is usually a very cumbersome task because they change class-names and utility markup, which affects every page where Bootstrap markup is used (ie: every Admin page). But upgrading minor updates is mostly a drop-in-replacement of JS/CSS files.

- Font Awesome: https://fontawesome.com/
  - `includes/templates/responsive_classic/common/html_header.php`
  - `admin/includes/admin_html_head.php`
  - `admin/includes/stylesheet.css`

> CAUTION: Be mindful that upgrading FontAwesome between its "major" releases is usually a very cumbersome task because icon naming strategies may be different, which affects every page where FA icons are used (ie: numerous Admin pages, and Catalog templates). But upgrading minor updates is mostly a drop-in-replacement of some CSS files.


<div style="text-align:right;" id="next">
   <a class="btn btn-lg btn-primary mr-3 mb-4" href="/dev/release_process/prerequisites/">
        Next - Prerequisites<i class="fas fa-arrow-alt-circle-right ml-2"></i>
   </a>
</div>
