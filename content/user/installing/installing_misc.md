---
title: Miscellaneous Installing Questions
category: products 
weight: -1 
---

{{< misc >}} 

--- 

### How to Validate the Integrity of a Downloaded File (MD5 or SHA1 Checksums)

When downloading files from the internet, it's very important to verify that the file you downloaded IS in fact the file you EXPECTED to download. Authors of software typically zip up their software and then calculate a "checksum" based on the contents, and post that checksum next to the link to download the file. YOU should then re-calculate the checksum on the file AFTER downloading, and compare to be sure that the checksum YOU calculated matches the one posted by the author. If they don't match, then you should NOT use the downloaded file, because it may have been tampered with. In such cases you should also report the discrepancy to the author so they can investigate the tampering or fix a mistake.

See [the useful tools page](/user/first_steps/useful_tools/#hash-validation-tools) for a list of checksum validation tools. 

---

### What is CHMOD and what do the numbers mean?

**Background:** The recommended permission for configure.php files is 444. 
A number of hosts do not allow setting permissions to 644 for some reason (mine included). Setting to 444 is perfectly acceptable. If you should need to modify the file you may need to temporarily change the permissions to something like 755 while you make the modification. Be sure that when you are finished modifying the file to set it back to 444 so as to prevent others from being able to mess with it (security issue).


Here is what the numbers mean:

```
444 = (r-- r-- r--): owner/group/others are all only able to read the file. They cannot write to it or execute it.
644 = (rw- r-- r--): same as 444 except the owner can write to it.
755 = (rwx r-x r-x): owner can read, write and execute the file, members in the user group and others can read and execute the file but cannot write to it.
```

r = read, w = write and x = execute.

In the format above, the first group of three characters represents the owner's level of permission, the second group represents permission for others in the same user group as the owner, and the final 3 characters represent the permission for all others (including website visitors).

If you were able to set to 644 the owner (you) could modify the file while all others would be restricted. In that case you would not need to change permissions in order to modify it. Just leave it at 644.

The permissions are set on the host server usually through the user's control panel. They can also be set using the chmod command in many [FTP tools](/user/first_steps/useful_tools/#ftp-tools), or or through SSH access to the server, if available. 

This article on [file permissions](/user/installing/permissions/) goes into more detail.

---

### Connection to Database failed ... Access denied for user: 'myname@localhost' (Using password: YES)

This suggests you have something wrong with any of:

- username
- password
- database name
- database host/server
- security settings on your database

When you created your database, did you grant the user access to the database?

Proper database-configuration includes:

- make a database
- make a user, with password
- grant the user permission to use the database

See also [How do I create a MySQL database for Zen Cart?](/user/installing/create_mysql_database/) 

Specific steps for creating and securing a database on your server can be obtained from your hosting company tech support.

---
### Is it possible to create/build a complete Zen-Cart setup on a test server and then install on a live server?
 
Yes - follow the guidance in [moving your cart to a new server](/user/installing/change_hoster/). 

---
<!-- please keep this at the end --> 
{{< faq_questions >}}
