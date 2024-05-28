---
title: Admin Dashboard 
description: The Admin Home Page 
category: admin_pages
weight: 480 
---

The Admin Dashboard is your home page in the Zen Cart admin.  

It is structured to give you the maximum amount of information possible about 
your store one one page.  

Each of the boxes on the admin page under the menu is called a widget. 
Here's the statistics widget, as an example. 

![Widgets on home page](/images/widget.png)

The following widgets are pre-built on your admin home page: 

- Statistics (product and category counts, reviews, etc.)
- Special, Featured and Sale counts
- Order counts by status
- New Customers
- Who's Online 
- Visitor History 
- New Orders 
- Monthly Sales

## Customizing 

- You may modify the position of each widget on the screen, or delete widgets that are not useful to you. 
  - In Zen Cart 2.0.1 and above, you may customize the dashboard by modifying the `$widgets` array created in `admin/index_dashboard.php` using the [notifier](/dev/code/notifiers/) `NOTIFY_ADMIN_DASHBOARD_WIDGETS`.
  - In older versions of Zen Cart, you you may customize the dashboard by changing the inclusion order of the widgets in `admin/index_dashboard.php`.

- If you have specific things you'd like to monitor on your site, you can build your own widget.  See [building an admin widget](/dev/code/widget/) for details. 
- Some parameterization of dashboard New Orders widget may be performed using the [Admin Site Specific Overrides](/user/admin/site_specific_overrides/).

