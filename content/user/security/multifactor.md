---
title: Multi-factor authentication in Zen Cart 
description: Using two-factor authentication for admin access 
category: security
weight: 10
---

Zen Cart 2.1.0 introduces multi-factor authentication (MFA) for access to the **admin area**.

To be clear: It is only used for accessing the **admin area**. 
Customers shopping on your storefront are not affected by it.

MFA is a common requirement for PCI / PA-DSS compliance, especially if your admin area controls access to payment methods and customer subscriptions.

## Turning on MFA for the site
Multifactor authentication may be enabled on the [Admin > Configuration > My Store](/user/admin_pages/configuration/configuration_mystore/) page. 

Once enabled for the site, multifactor authentication must be used by each Admin user when logging in, starting immediately with their next login.

## Configuring MFA, per-user
Each admin user will set up their own MFA individually. You have a choice of authentication methods: 

- Using Google Authenticator or another similar One-Time-Passcode-compatible app (examples: Google Authenticator, Microsoft Authenticator, 1Password, LastPass Authenticator, Duo Mobile, etc)
- Receiving a code by email at every login attempt

## Resetting MFA for a specific user
If an Admin user has set up MFA on their account but they're having trouble using it and need to reset it to set it up fresh again (or changed MFA apps and need to set it up new), or wish to switch MFA methods (app vs email), you can use the Reset button next to their name on the [Admin > Admins > Admin Users](user/admin_pages/admins/admin_users/) screen.
Simply click the Reset button, and then click the Confirm button.

This will clear all prior MFA codes for their account (meaning they should delete all old MFA setups for your Admin area, within their One-Time-passcode apps).

At next login they will be prompted to set up MFA fresh again.

## Disabling MFA for a specific user
You may disable MFA per-user on the [Admin > Admins > Admin Users](user/admin_pages/admins/admin_users/) screen.  

If they have MFA set up on their account already, you can use the Reset button (and confirm) to remove it. 

Then click the Exempt button.  This will disable MFA for the selected user, starting with their next login. Only their password will be required, as usual.

NOTE: 3rd-party logins, particularly those that are automated via external services, will require this Exemption process. 
Example: ShipStation's plugin logs into your store using its own Admin User account, but since it's automated it won't be able to use MFA. Simple Exempt that user for it to work.


## Turning off MFA for the entire site
If after using MFA you decide you don't want to use it any more, you may either exempt individual users (see above), or turn it off for all users on the Admin > Configuration > My Store screen.

