Introduction
============

Admin action classes are a new way of writing code for admin pages. Previously admin pages were called using a URL like `http://localhost/admin_dir/categories.php` and each page was a mixture of procedural php and html.

Zen Cart v2 allows you to write code that is object oriented and separates code from html.

It does this by using a similar URL structure to catalog (storefront). Instead of accessing code for a 'page' directly, it uses a `front controller`.
e.g the URL `http://localhost/admin_dir/categories.php` would be written as `http://localhost/admin_dir/index.php?cmd=categories`

Two things to note here.

1) You don't need to manually create these links in your code. The admin version of `zen_href_link()` will create them automatically, so there are no changes required to existing code if you're already using `zen_href_link()` correctly.

2) The controller supports legacy code, such that if an admin action class for `categories` does not exist it will default back to using `admin_dir/categories.php`

Admin action classes are stored in the `/includes/library/zencart/Controllers/src/admin/` directory

The action class must extend one of the abstract base admin classes, currently either `AbstractController` or `AbstractLeadController`


How it works
============

`admin/index.php` is replaced by code that provides a minimal front controller. The code in `admin/index.php` looks at the URL and sees if there is a `'cmd'` parameter. If not, it assumes this is a legacy URL e.g. `http://localhost/admin/categories.php` and does a redirect to set the 'cmd' parameter e.g. to `cmd=categories`

If the `'cmd'` parameter does exist, it checks to see if an action class exists in `admin/includes/classes/actions/admin`

If an action class exists it will load it, and call the class's `'invoke'` method. The `invoke` method checks whether an `'action'` parameter exists in the URL and if so calls a method in the action class based on the `'action'` parameter.

e.g. if the 'action' parameter = 'insert' then the `insertExecute` method of the action class will be called.

If no 'action' parameter exists then the default `mainExecute` method will be called.

If an action class does not exist, then again it assumes that we are trying to load legacy code. e.g. if `cmd=categories` it will load `admin/categories.php`

As mentioned earlier, Admin action classes should extend the `AbstractController` class, or another class that has `AbstractController` as its ultimate parent.
