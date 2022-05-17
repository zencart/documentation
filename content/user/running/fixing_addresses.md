---
title: Fixing Physical Addresses
description: Fixing Customer Shipping and Billing Addresses in Zen Cart 
category: Running
weight: 10
---

Sometimes customers enter the wrong shipping address.  Often this is caused by a browser accidentally autofilling a field, and sometimes it's just finger trouble. 

Go to `Admin > Customers > Customers`, and search for the customer's record.
If you see a link next to the customer's id, it means they have multiple address book records.  In other words, the billing and shipping addresses might be different. 

![Customer Addresses](/images/customer_search.png)

If you need to edit their billing address, just edit the customer record.

If they have a different shipping address, and you need to edit it, the best way to do this is to login as the customer.  

If the `Admin > Customers > Customers` screen has a *Place Order* button on the right hand side in the sidebox, press it.  Login as the customer and go to the My Account Page, and click the link titled `View or change entries in my address book`.  See [login as customer](/user/running/login_as_customer/) for more details on how to do this. 

If you do not have a *Place Order* button, you will need to install and use one of the [Master Password](/user/admin/master_password/) plugins.  Login using the customer's email address and the master password, and edit their address book.  
