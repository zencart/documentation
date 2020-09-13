---
title: What is CHMOD? 
description: What do those 3 digits mean?
category: installing 
weight: 10
---

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

