---
title: Audiences 
description: What is an audience in Zen Cart? 
category: email
weight: 10
---

Zen Cart contains a table called `query_builder` which contains queries that are used to build lists of email addresses for the [Send Email](/user/admin_pages/tools/send_email/) and [Newsletter Manager](/user/admin_pages/tools/newsletter/) functions. 

There is no admin panel interface to this table, but new audiences may be created by copying existing rows and updating as needed.  For example, a list of all newsletter subscribers who have purchased in the last year could be made by copying "Active customers in past 3 months (Subscribers)" and adjusting the query_name, query_description and query_string values in the new row.

It can be helpful to turn on [Audience-Select Count Display](/user/admin_pages/configuration/configuration_email/#audienceselect_count_display) while doing this to see the size of the created lists. 

You can also use plugins like [Email Address Exporter](/user/email/exporting_email_addresses/) to build email lists based on audiences. 

