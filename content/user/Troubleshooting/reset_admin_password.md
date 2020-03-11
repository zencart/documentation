---
title: Admin Password - Resetting or Changing
category: troubleshooting
weight: 1
---
## 1. Log in with another account. 
If you can log in to your Zen Cart admin using another account,  please do so, and reset/modify the other admin password as needed via  Admin-&gt;Tools-&gt;Admin Settings<br>
 <br>
<br>

## 2. Delete the old user and add a new one. 
If you can't remember your admin account or password, there's still hope.<br>
The first thing you can try is to click the "Resend Password" button and enter the admin email address.<br>
If for some reason that doesn't work for you, you can create a temporary admin account in order to log in. <br>
 <h3>In v1.5.x use this:</h3> Open your phpMyAdmin (supplied by your hosting company), select your   store's database, then click the "SQL" tab and run this query: 
	<pre class="bbcode_code" style="height:60px;"><font size="2">DELETE FROM <font color="#0000ff">admin</font> WHERE admin_name = 'Admin'; 
INSERT INTO <font color="#0000ff">admin</font> (admin_name, admin_email, admin_pass, admin_profile) 
VALUES ('Admin', 'admin@localhost', '351683ea4e19efe34874b501fdbf9792:9b', 1);</font></pre>

<b>NOTE</b>: If you are using a prefix for your database tables,</font> you'll naturally need to add that prefix to the table name above. <br>
ie. "DELETE FROM <font color="#0000ff">prefix_admin</font> ... " and "INSERT INTO <font color="#0000ff">prefix_admin</font> ..." ... replacing `prefix_` with your actual tablename prefix.<br>
<br>
<b>Getting an error like this?</b> <font color="#ff0000">"1146 - Table 'myaccountname.admin doesn't exist"</font>. This means you need to add the prefix, as described in the NOTE above.<br>
<br>
 <h3>In v1.3.9 and older, use this:</h3> Open your phpMyAdmin (supplied by your hosting company), select your   store's database, then click the "SQL" tab and run this query:<br>

	<pre class="bbcode_code" style="height:60px;"><font size="2">DELETE FROM admin WHERE admin_name = 'Admin'; 
INSERT INTO admin (admin_name, admin_email, admin_pass, admin_level) 
VALUES ('Admin', 'admin@localhost', '351683ea4e19efe34874b501fdbf9792:9b', 1);</font></pre>
If you are using a prefix for your database tables, you'll naturally need to add that prefix to the table name above. <br>
ie. "... FROM/INTO prefix_admin ...".<br>
 -------<br>
<br>
<b>You should now be able to login using the following details: <br>
</b><b>Username: Admin<br>
 Password: admin </b><br><br />

Be sure to use proper case. ie. 'Admin' for username, not 'admin'. <br>
In v1.5.0 and newer, you will be prompted to change the password right away.<br>
<br>
 <br>
 After you log in, remember to delete this temporary admin account after creating a new one.<br>
In v1.5.x you'll do that under the Admin Access Management tab.<br>
In v1.3.x and older, it's under the Tools-&gt;Admin Settings option.
