---
title: Place Order
description: Creating an order on behalf of a Customer in Zen Cart 
category: Running
weight: 10
---

The **Place Order** button in the Admin > Customers > Customers screen allows an administrator to log into a customer’s account.

This can be particularly helpful in cases where:

- you want to assist a customer over the phone but need to see what they've already put in their shopping basket
- you are taking an order for a customer over the phone and need to login as them
- they are having some sort of technical issues inside their account and you need to "see" it yourself

**NOTE:** Only authorized Administrators may use this feature.

**NOTE:** Prior to Zen Cart version 1.5.7 this feature required a separate plugin installation. See below for options with older versions.

#### Setup / Configuration

After logging into your Store Admin, go to Configuration > My Store
There are 3 settings that can be configured to allow Login As Customer:

- Customer PLACE ORDER: Single AdminID 
- Customer PLACE ORDER: Admin ProfileID
- Customer PLACE ORDER: Passwordless Login 

The ProfileID is shown in the [Admin Profiles](/user/admin_pages/admins/admin_profiles/) screen. 
The AdminID is shown in the [Admin Users](/user/admin_pages/admins/admin_users/) screen.

**Single Admin ID** allows the Admin User ID (Admin > Admins > Admin Users ) to log in to the customer’s account using the password associated with that admin ID as long as the Admin Profile for that Admin ID allows access to Customers > Customers in the admin profile setup.

**Admin ProfileID** allows any Admin Profile ID (Admin > Admins > Admin Profiles ) to login to the customer’s account as long as the Admin Profile is allowed access to Customers/Customers in the admin profile setup.  Setting this value to 1 (where 1 is the default admin profile ID for SuperUser) will allow all superusers to login as customers. 

**Passwordless Login** True allows direct access to the customer’s account from within Admin without using a password. This may have PCI security concerns, so use with caution. The default setting is FALSE.

These settings can be utilized in any combination, use of one is not mutually exclusive of the other.

ALSO: For a given admin profile they must be given access to the Customers page (checkbox) in order to use the "Place Order" button from the Admin side.
If the logged in Admin person is not allowed access due to the admin profile, there will be no “Place Order” button shown. 


#### Using 

Admins can access any customer’s account directly from the Admin Customers list by using the “Place Order” button that is shown in the sidebar of Admin > Customers > Customers. 

<img src="/images/login_as_customer.png" alt="Login as Customer" />
<br><br>

Admins can login as customer directly from the public website using the customer's email address and any Admin password that is associated with an admin profile that allows access.
> Note: Once you arrive at the customer login screen, ANY allowed Admin Password can be used, not just the password of the current admin.

Once logged into the customer’s account, the admin can place orders, view and change anything that the customer can edit within their account as well as “PLACE ORDER” as/for the customer.


### Prior to Zen Cart 1.5.7

In older Zen Cart versions a plugin is required in order to login as a customer.  The following options are available:

- Master Password
- Admin Login as Customer
- Encrypted Master Password

These plugins are all available in the [Plugins Library](https://www.zen-cart.com/downloads.php). 


## What if the user doesn't have an account? 

- If they have an email address, you can simply create an account for them in the storefront using their email address and a randomly chosen password
- If they do not have an email address, you can just use an email address on your domain with a random password just to satisfy the requirement for an email address.  For example, if your customer's name was Scott Wilson, you could create an account with the email scott.wilson@YOURDOMAIN.com.  Just be sure to turn off newsletters and other emails going to this account, since they will all bounce.  See [fabricating email addresses](/user/email/fabricating_email_addresses/). 

