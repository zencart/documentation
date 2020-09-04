---
title: Long EZ-Pages are getting cut off
description: Is there a size limit to EZ-Pages?
category: ezpages
weight: 10
---

EZ-Pages are stored in your database. The field that contains the HTML can store approximately 65,000 characters - anything after that will be lost.

To store more you have two options:
1. increase the size of this database field or
2. hold the information on a new page outside of the database

To increase the size of the database field, you would use your database management tool (e.g. phpMyAdmin) to open the `ezpages_content` table (or the `ezpages` table in Zen Cart 1.5.5 and below), and then change the field type for `pages_html_text` from `TEXT` to `MEDIUMTEXT`. This will give it a capacity of 16 million characters. If that's not enough (wow, what are you doing!) then you can change it to `LONGTEXT` which will give you a cool 4 trillion characters with which to play.

Alternatively you could use the [extra pages](/user/template/extra_pages) (`page_2`, `page_3` and `page_4`) which are shipped with Zen Cart and customize them as described in 
[title change for page_X](/user/new_user_topics/title_change_for_page_x/). This would be slightly more complex, but offer quicker performance and more flexibility.
