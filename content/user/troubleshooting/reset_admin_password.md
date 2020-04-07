---
title: Admin Password - Resetting or Changing
description: Zen Cart Admin Password - Resetting or Changing
category: troubleshooting
weight: 10
---
## 1. Log in with another account. 
If you can log in to your Zen Cart admin using another account,  please do so, and reset/modify the other admin password as needed via  Admin > Tools > Admin Settings<br>
<br>
<br>

## 2. Delete the old user and add a new one. 
If you can't remember your admin account or password, there's still hope.<br>
The first thing you can try is to click the "Resend Password" button and enter the admin email address.<br>
If for some reason that doesn't work for you, you can create a temporary admin account in order to log in. <br>
Open your phpMyAdmin (supplied by your hosting company), select your   store's database, then click the "SQL" tab and run this query: 

```
DELETE FROM admin WHERE admin_name = 'Admin'; 
INSERT INTO admin (admin_name, admin_email, admin_pass, admin_profile) 
VALUES ('Admin', 'admin@localhost', '351683ea4e19efe34874b501fdbf9792:9b', 1);
```

**NOTE**: If you are using a prefix for your database tables, you'll naturally need to add that prefix to the table name above. <br>
ie. 

`DELETE FROM prefix_admin` and `INSERT INTO prefix_admin`, replacing `prefix_` with your actual tablename prefix.

<b>You should now be able to login using the following details: <br>
</b><b>Username: Admin<br>
 Password: admin </b><br><br />

Be sure to use proper case. ie. 'Admin' for username, not 'admin'. <br>
You will be prompted to change the password right away.<br>
<br>
After you log in, remember to delete this temporary admin account after creating a new one. See the Admin Access Management tab.<br>
