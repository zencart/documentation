---
title: Timezone (TZ) setting 
description: I want to use local time, not GMT 
category: new_user_topics
weight: 10
---

To set the correct time zone for your store, set the $TZ value in
the file `includes/extra_configures/set_time_zone.php` to [your timezone](https://www.php.net/manual/en/timezones.php). 

For example, if you live on the East Coast of the United States, you would use 

```
   $TZ = 'America/New_York'; 
```


In versions prior to Zen Cart 1.5.2, see [this forum post](https://www.zen-cart.com/showthread.php?208662-date-timezone-patch-for-v1-5-1).  But you should really [upgrade](/user/upgrading/). 
