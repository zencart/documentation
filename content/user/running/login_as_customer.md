---
title: Login as Customer 
description: Logging in as a Customer in Zen Cart 
category: Running
weight: 10
---

### Zen Cart 1.5.7 and above 
In Zen Cart 1.5.7 and above, login as customer is a built-in capability. 

Just as the name indicates, Login As Customer allows Admin profileID / AdminID to log into a customer’s account from either ZC Admin or the public website if the customer’s email address is known. Prior to zc157, this feature requires a separate plugin installation.

Configuration:

After logging into the ZC Admin, go to Configuration > My Store
There are 3 settings that can be configured to allow Login As Customer


- Customer PLACE ORDER: Single AdminID Default: 0 (no access)
- Customer PLACE ORDER: Admin ProfileID Default 0 (no access)
- Customer PLACE ORDER: Passwordless Login True/False

Single Admin ID allows the Admin User ID (Admin > Admins > Admin Users ) to log in to the customer’s account using the password associated with that admin ID as long as the Admin Profile for that Admin ID allows access to Customers > Customers in the admin profile setup.

Admin ProfileID allows any Admin Profile ID (Admin > Admins > Admin Profiles ) to login to the customer’s account as long as the Admin Profile is allowed access to Customers/Customers in the admin profile setup.

Passwordless Login True allows direct access to the customer’s account from within Admin without using a password. This may have PCI security concerns, so use with caution. The default setting is FALSE.
These settings can be utilized in any combination, use of one is not mutually exclusive of the other.
Use:
Admins can access any customer’s account directly via ZC Admin by using the “Place Order” button that is shown IF the currently logged in admin’s profile allows access. If the Admin logged in is not allowed access due to the admin profile, there will be no “Place Order” button shown. Note: Once you arrive at the customer login screen, ANY allowed Admin Password can be used, not just the password of the current admin.

Admins can login as customer directly from the public website using the customer's email address and any Admin password that is associated with an admin profile that allows access.

Once logged into the customer’s account, the admin can place orders, view and change anything that the customer can edit within their account as well as “PLACE ORDER” as/for the customer.

### Prior to 1.5.7 

A mod is required to login as a customer.  The following options are available:

- Master Password
- Admin Login as Customer
- Encrypted Master Password

These mods are all available in the [plugins area](https://www.zen-cart.com/downloads.php). 
