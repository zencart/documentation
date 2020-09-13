---
title: What does "Connection to Database failed" mean? 
description: I get the message "Access denied for user myname@localhost" 
category: installing 
weight: 10
---
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

