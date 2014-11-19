Introduction
============

Admin action classes are a new way of writing code for admin pages. Previously admin pages were called using a URL like http://localhost/admin_dir/categories.php and each page was a mixture of procedural php and html.

Zen Cart v1.6 allows you to write code that is  object oriented and separates code from HTML.

It does this by using a similar URL structure to catalog. Instead of accessing code for a 'page' directly, it uses a front controller.
e.g the URL http://localhost/admin_dir/categories.php would be written as http://localhost/admin_dir/index.php?cmd=categories

Two things to note here.

1) You don't need to manually create these links. The admin version of zen_href_link will create them automatically.

2) The controller supports legacy code, such that if an admin action class for categories does not exist it will default back to using admin_dir/categories.php

admin action classes are created in the admin_dir/includes/classes/actions/admin/ directory

The class must extend one of the abstract base admin classes, currently either zcActionAdminBase or zcActionAdminLeadBase
