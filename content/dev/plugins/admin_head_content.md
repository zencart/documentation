---
title: Admin HEAD content 
description: New standards for head element in admin files 
category: plugins
weight: 10
---

Starting in Zen Cart 1.5.7, a new file `admin/includes/admin_html_head.php` was introduced to consolidate the code required to build the `<head>` element in an admin page.  This includes such things as: 

- setting the page title 
- pulling in stylesheets
- including any needed javascript

In prior versions, the code to do this was replicated on each admin page.

Since then, admin pages have updated over time to remove the replicated blocks of code in favor of a single inclusion of `admin_html_head.php`.  As of Zen Cart 2.0.0, this change is complete, and older files used by the old method have been deprecated.  This includes: 

- `admin/includes/menu.css`
- `admin/includes/menu.js`
- `admin/includes/stylesheet.css`

Some older plugins may still use these files.  Migrating to the new standard is straightforward; simply replace the old contents of the `<head>` element by a reference to `admin_html_head.php`.


![Admin HTML Header change example 1](/images/admin_html_head.png)


![Admin HTML Header change example 2](/images/admin_html_head_2.png)

You will also want to remove references to the old `init()` javascript function. 

![Admin HTML Header change example 3](/images/admin_html_head_3.png)


If you maintain a plugin which needs to work on both older and newer versions of Zen Cart simultaneously, see [this forum post](https://www.zen-cart.com/showthread.php?229611-Plugin-Maintainers-Important-details-for-Zen-Cart-2-0-0&p=1396050#post1396050) for an example block of code that can be used to support both.

