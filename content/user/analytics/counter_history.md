---
title: What do the numbers in the Counter History box mean?
description: Understanding admin counter history 
category: analytics
aliases:
    - /user/admin/counter_history
weight: 10
---

The counter counts two things:

Session count is the number of first hits to your site based on unique browser sessions.  This is approximately the number of visits that day. 

**NOTE:** this does not distinguish between someone coming to your site at 9:00am and then returning with a new session at 3:00pm on the same day

The Total is the number of pages viewed.  This counts how many pages does the customer actually go to during that session.

The database actually contains all the days of the year, unless you delete them manually. 

The display on the Admin Home page will be for the last 10 days.  It will roll over by itself as the site is used.

### What about Google Analytics differences?
Google analytics holds a cookie for 24 hours, so re-visitors are not counted within that time frame. Zen Cart does not.

