---
title: Admin Password - Resetting or Changing
description: Admin password not working?  Try these steps. 
category: troubleshooting
weight: 10
aliases:
    - /user/admin/admin_password/
---

## 1. Log in with another account. 
If you can log in to your Zen Cart admin using another account,  please do so, and reset/modify the other admin password as needed using the [Admins > Admin Users](/user/admin_pages/admins/admin_users/) page.

## 2. Resend Password 
If you can't login from another account, try using the *Resend Password* button on the admin login page. 
Enter the admin email address, and wait for your new password to arrive by email. 

## 3. Use phpMyAdmin 
If the techniques above don't work, use phpMyAdmin to create a 
temporary admin user. 
Open your phpMyAdmin (supplied by your hosting company), select your store's database, then click the "SQL" tab.  Run this query: 

```
DELETE FROM admin WHERE admin_name = 'Admin'; 
INSERT INTO admin (admin_name, admin_email, admin_pass, admin_profile) 
VALUES ('Admin', 'admin@localhost', '351683ea4e19efe34874b501fdbf9792:9b', 1);
```

**NOTE**: If you are using a prefix for your database tables, you'll naturally need to add that prefix to the table name above.  For example, if your prefix is `zc_`, you would use 

`DELETE FROM zc_admin` and `INSERT INTO zc_admin` in the commands above. 

> **NOTE**: If you are using a very old version of Zen Cart then the field names above may be different than your database has. See https://www.zen-cart.com/content.php?44-how-do-i-change-or-reset-my-admin-password for additional information.

<b>You should now be able to login using the following details: <br>
</b><b>Username: Admin<br>
 Password: admin </b><br><br />

Be sure to use proper case. ie. 'Admin' for username, not 'admin'. <br>
You will be prompted to change the password right away.<br>
<br>
After you log in, remember to delete this temporary admin account after creating a new one. See the [Admins > Admin Users](/user/admin_pages/admins/admin_users/) page.

