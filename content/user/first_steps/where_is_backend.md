---
title: Where is the Admin / Back-end / Control Panel interface? 
description: I don't have an "/admin" folder!
category: first_steps 
weight: 10
---

You can access the Zen Cart admin area using your browser by pointing it to:


```
http://WWW.YOURSITE.COM/admin-foldername/index.php
```


or, if you installed your site in a [subfolder](/user/installing/subfolder/), like this:

```
http://WWW.YOURSITE.COM/subfolder/admin-foldername/index.php
```


Out-of-the-box, the admin foldername is `admin`, but the system requires you to change that on first install, because any hacker can guess "admin", or read this very article you're reading to discover the word "admin".  

See the instructions for [renaming the admin folder for security reasons](/user/installing/rename_admin/). 

**WHAT IF I DON'T KNOW MY ADMIN FOLDER NAME?**  

You will require access to the files on your webserver to find out the actual admin foldername. This is typically done via a secure [FTP tool](/user/first_steps/useful_tools/#ftp-tools), or via your browser by logging in to your hosting company's control panel and using their provided "file manager" to browse your site's files.  

The Zen Cart structure is like this:  

```
admin (which contains the following 3 folders and a bunch of .php files):
    - backups
    - images
    - includes  (looks a LOT like the other non-admin "includes" folder)
- cache
- download
- editors
- email
- images
- includes
- logs
- media
- index.php
- ipn_main_handler.php
- nddbc.html
```

