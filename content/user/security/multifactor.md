---
title: Multi-factor authentication in Zen Cart 
description: Using two-factor authentication for admin access 
category: security
weight: 10
---

Zen Cart 2.1.0 introduces multi-factor authentication (MFA) for access to the admin.

Multifactor authentication may be enabled on the [Admin > Configuration > My Store](/user/admin_pages/configuration/configuration_mystore/) page.  

Once this is done, multifactor authentication must be enabled on a per user basis.  To do this, logout from the admin and log back in.  You have a choice of authentication methods: 

- Receiving a code by email
- Using Google Authenticator

If after using MFA you decide you don't want to use it any more, you may either turn it off for all users on the Admin > Configuration > My Store screen, or disable it per user on the [Admin > Admins > Admin Users](user/admin_pages/admins/admin_users/) screen.  

Click the Reset button and confirm, then click the Exempt button.  This will disable MFA for the selected user.


