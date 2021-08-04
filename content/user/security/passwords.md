---
title: Passwords in Zen Cart 
description: Rules for passwords in Zen Cart
category: security
weight: 10
---

### Customer Passwords 
The only requirement for customer passwords in Zen Cart is that the length of a password must be greater than or equal to `ENTRY_PASSWORD_MIN_LENGTH`, which is set on the [Admin > Configuration > Minimum Values](/user/admin_pages/configuration/configuration_minimumvalues/) screen.

### Admin Passwords
Admin Passwords must meet the following requirements: 
- The length of an admin password must be greater than or equal to `ADMIN_PASSWORD_MIN_LENGTH` (which has a minimum value of 7). 
- Admin passwords must contain at least 1 letter and 1 number.
- Admin passwords must not be the same as the last 4 passwords (unless `PADSS_PWD_EXPIRY_ENFORCED` is disabled). 
- Admin passwords must be changed every 90 days (unless `PADSS_PWD_EXPIRY_ENFORCED` is disabled). 

### Disabling Admin Password checks 

Disabling this check makes your site makes your site NON-COMPLIANT with PA-DSS rules. Disabling should only be used by developers who are working on sites that are not available over the public Internet.

The setting `PADSS_PWD_EXPIRY_ENFORCED` is on the screen [Admin > Configuration > My Store](/admin_pages/configuration/configuration_mystore). 

### Changing Customer Passwords
- Customers may change their own passwords using the screen My Account > Change my Account Password.
- Customers may reset their passwords using the "Forgot your password" link on the login page.
- Since 1.5.5, admins may reset customer passwords from the [Admin > Customers > Customers](/user/admin_pages/customers/customers/) screen.

### Changing Admin Passwords 
- Admins may change their own passwords (or the passwords of other admins) using the screen Admins > Admin Users. 
- Admins are forced to change their own passwords every 90 days as noted above. 
- Admins may reset their passwords using the "Forgot Password?" link on the login page.
- More advanced troubleshooting tips for changing admin passwords are provided in the FAQ [Admin Password - Resetting or Changing](/user/troubleshooting/reset_admin_password/).

### Database Passwords 
The password pair for database access is contained in the value `DB_SERVER_PASSWORD`, which is set in the files `includes/configure.php` and `admin/includes/configure.php`.  Your hosting company may have rules for these passwords. 

Some plugins such as [Backup MySQL Plugin](https://www.zen-cart.com/downloads.php?do=file&id=7) use the database password in a shell command.  In this case, the password must not use shell metacharacters. 

