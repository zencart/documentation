---
title: Admin Activity Logs 
category: admin_pages
weight: 40 
---

Admin Activity Logs allows you to access the logging data which is 
created when actions are taken in the admin.  This can be used as a 
security audit or to figure out when an undesired change was made. 

You cannot directly view your admin activity logs on this page.  To view this table, you will have to use phpMyAdmin, or 
export a CSV, and download the output to your own computer. 

When viewing this data, note that the field `gzpost` is a json-encoded blob, so you will not be able to view it directly in phpMyAdmin or in a phpMyAdmin export.  However, using the Export feature built into this page (at the top) will allow you to view the gzpost data. 

![Admin Activity Log Manager](/images/admin_activity_logs.png) 

### Purging Logs

If you are receiving the message, "The Admin Activity Logs table has records over 2 months old and should be archived to conserve space" 

![Zen Cart Admin Activity Log button](/images/admin_activity_log.png) 

this is what you should do: 

a) Go to Admins > Admin Activity Logs.  Where it says, "Review or Export Logs," check the box that says "Save to file on server" and press the *Go* button
on the right.  This will save your logs to disk in case you need them for troubleshooting.  The recommended retention period is 12 months. 

b) At the bottom of the screen, press the *Reset* button.  This will
take you to the Admin Activity Log Manager manager page.  On this page, 
press *Reset* again to delete your logs.  

