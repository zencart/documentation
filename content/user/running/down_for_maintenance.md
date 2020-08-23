---
title: Down for Maintenance 
description: Turning your Zen Cart store off for a time
category: Running
weight: 10
---

There are a few situations where you might want to take your store offline: 

- Performing backups 
- Disruption of business due to personal emergency
- [Moving your website to another hoster](/user/installing/change_hoster/)
- Updating your stock counts if you [track inventory](/user/running/stock/) 

The configuration screen [Admin > Configuration > Website Maintenance](/user/admin_pages/configuration/configuration_websitemaintenance/) allows you to put your store in maintenance mode and controls how your store appears to customers when it is down for maintenance.

The behavior of a store which is down for maintenance is as follows:

- Customers will only see your home page; they are not permitted to browse.
- You may restrict their view of the store further if desired.  For example, you can turn off sideboxes or hide prices as well; see the possibilities on the Website Maintenance configuration page. 

Here's what a site might look like in down for maintenance mode: 

![Down for Maintenance](/images/dfm1.png)

<br><br>

You could turn off the sideboxes during down for maintenance, and it would look like this:

![Down for Maintenance - no sideboxes](/images/dfm2.png)

As the storeowner, you may want to still be able to browse your store while it is in maintenance mode.  To do so, go to `Admin > Configuration > Website Maintenance`, and add your IP to the list in the `Down For Maintenance (exclude this IP-Address)` field.
