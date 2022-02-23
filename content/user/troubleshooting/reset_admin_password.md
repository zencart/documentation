---
title: Admin Password - Resetting or Changing
description: Reset your admin password using these steps
category: troubleshooting
weight: 10
aliases:
    - /user/admin/admin_password/
---

If you [can't login to your admin](/user/troubleshooting/cant_login/), you may need to reset your admin password. 

## 1. Login and change it directly
If you are able to login to your Admin, and merely want to change your password, simply login, then go to the "Account" menu and change your password there.

## 2. Log in with another account. 
If you can log in to your Zen Cart admin using another account (with Super-User privilege), please do so, and reset/modify the other admin password as needed using the [Admins > Admin Users](/user/admin_pages/admins/admin_users/) page.

## 3. Forgot Password 
If you can't login from another account, try using the *Forgot Password* button on the admin login page. 
Enter the admin email address, and wait for your new password to arrive by email. 

## 4. Watch out for possible stumbling blocks 

- <b>Temporary Lockout:</b> If you accidentally type the wrong password twice (which can easily happen if you're tired or distracted), remember that if you type the wrong password a third time, you get locked out of your admin account for 30 minutes - and the system won't tell you this because it assumes you're a bad guy trying to break in.
- <b>Password Managers:</b> If you are using a [password manager](/user/first_steps/security/#use-a-password-manager), the password manager *may* be overwriting what you are filling in so your password change doesn't work.  Try changing your password in a browser where you are not running (or logged out of) your password manager, and then save your new password in your password manager.
- <b>www vs non-www:</b> Your hoster may be configured to redirect `www.mystore.com` to `mystore.com`.  If this is the case, you will want to specify the non-www site (i.e. `https://mystore.com`) in your `admin/includes/configure.php` file. 
- <b>Browser Plugins:</b> The same advice applies with other browser plugins - they might be breaking the Zen Cart admin login.  Try a browser you don't normally use and see if you can login successfully there. 

## 5. Use phpMyAdmin 
If the techniques above don't work, use phpMyAdmin to create a temporary admin user directly in the database. You must have database control to do this.
Open your phpMyAdmin (supplied by your hosting company), select your store's database, then click the "SQL" tab.  Run this query: 

```
DELETE FROM admin WHERE admin_name = 'Admin'; 
INSERT INTO admin (admin_name, admin_email, admin_pass, admin_profile) 
VALUES ('Admin', 'admin@localhost', '351683ea4e19efe34874b501fdbf9792:9b', 1);
```

**NOTE**: If you are using a prefix for your database tables, you'll naturally need to add that prefix to the table name above.  For example, if your prefix is `zc_`, you would use 

`DELETE FROM zc_admin` and `INSERT INTO zc_admin` in the commands above. 

> **NOTE**: If you are using a very old version of Zen Cart then the field names above may be different than your database has. See https://www.zen-cart.com/content.php?44-how-do-i-change-or-reset-my-admin-password for additional information.

<b>You should now be able to login using the following details:</b><br>
<b>Username: Admin</b><br>
<b>Password: admin </b><br><br />

Be sure to use proper case. ie. 'Admin' for username, not 'admin'.

You will be prompted to change the password right away.

After you log in, remember to delete this temporary admin account after creating a new one. See the [Admins > Admin Users](/user/admin_pages/admins/admin_users/) page.

NOTE: If you are working with an old database, you may get a message that looks like 

```
#1292 - Incorrect datetime value: '0000-00-00 00:00:00' for column 'pwd_last_change_date' at row 1
```

When this happens, you have to fix the `admin` table before doing the INSERT. Use the command

```
ALTER TABLE admin MODIFY COLUMN pwd_last_change_date datetime NOT NULL default '0001-01-01 00:00:00', MODIFY COLUMN last_modified datetime NOT NULL default '0001-01-01 00:00:00', MODIFY COLUMN last_login_date datetime NOT NULL default '0001-01-01 00:00:00', MODIFY COLUMN last_failed_attempt datetime NOT NULL default '0001-01-01 00:00:00';
```

(again, adding a prefix to the tablename `admin` if required).

