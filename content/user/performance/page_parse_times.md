---
title: Page Parse Times and Query Counts
description: Page Parse Times for Zen Cart 
category: performance
weight: 10
---

## What Are The Parse Time Numbers

If you have enabled the display of parse times, you will see some statistical information in the footer of your pages, which looks like this:  

> <span class="Code">Parse Time: 0.314 - Number of Queries: 446 - Query Time: 0.123679</span>

Here's what they mean, in reverse order:  

The SQL/**Query Time** is the time spent waiting for the database to return its requested information. In other words, it is the time it took for all the SQL queries to run, starting from the time of sending a query, until the results came back.  When the next query is sent, the timer starts again from where it left off, etc. After the final query, the number is shown.  

The **Number Of Queries** is a counter: the number of hits on the database in order to retrieve data for display on the particular page you're looking at.  

The page **Parse Time** is the time it took from when the first line of code in index.php started processing until the footer of your page was drawn. This includes the delays introduced by any SQL queries waiting on the database.  It is the sum of both Query Time and all the time it takes to request data from the database and process the information it receives back. So CPU time is the difference between Parse Time and Query Time.  

## Interpreting The Numbers

If Query Time is larger than, or almost as large as, Parse Time then it means that you have a major bottleneck in the database performance.  

If the Parse Time is very large and Query Time is small, then you have a bottleneck in CPU processing activities, commonly caused by running on a server that's serving too many websites at the same time, or has been hijacked by phishers or spammers sending a lot of spam emails.  

If both Query Time and Parse Time are almost the same, then the majority of the time is taken up by database activities. If those numbers are larger than 1 or 2 seconds, then your server could probably benefit from some tuning by the server administrator.  

## How To Enable/Disable Parse Time Display

If you wish to enable/disable the display of this information, you may change the setting by going to [Admin > Configuration > Logging](/user/admin_pages/configuration/configuration_logging/) and setting *Display The Page Parse Time*.
  
If you have enabled this setting but the numbers are not displaying on your storefront (by default they would show in the page footer), then your custom template has been altered to prevent the display, in which case you will need to add the required PHP code to handle the display or remove the CSS code that prevents the information from being visible. The PHP code can be found in the default templates that come with Zen Cart.  

