---
title: Old database convertions script (deprecated) 
description: Notes on utf8mb4-conversion.php
category: upgrading 
weight: 10
noindex: yes
---

{{< technical >}}

The old converter is the plugin [Convert db2utf8](https://www.zen-cart.com/downloads.php?do=file&id=1318) which was also stored in Github as [utf8mb4-converter](https://github.com/zencart/utf8mb4-converter).

Please note this older version of the converter is no longer recommended; see [Converting to UTF8](/user/upgrading/convert_to_utf8/) for up to date instructions. 

## Issues with the old converter under PHP 8
The old converter would fail silently when error conditions occurred if run under PHP 8.  The new converter has fixed this issue.

## Issues with the old converter (prior to 03/05/2021)

Versions of the old converter `utf8mb4-conversion.php` and the older version, which was called `latin1-to-utf8-conversion.php`, prior to 03/05/2021 had an issue with incorrectly removing default values during the conversion.  A script exists to fix this issue; see the section "Missing Defaults" in the readme file for [https://github.com/zencart/utf8mb4-converter](https://github.com/zencart/utf8mb4-converter). 

Please note this issue only affects people who ran versions of this script prior to 03/05/2021. 

You will know you have this issue if database insert operations are failing because fields don't have default values.  For example, creating a new admin will fail with 

```
--> PHP Fatal error: 1364:Field 'prev_pass1' doesn't have a default value :: INSERT INTO admin
SET admin_name = 'admin',
admin_email = 'help@thatsoftwareguy.com',
admin_pass = '....',
admin_profile = 1,
pwd_last_change_date = now(),
```
You can also tell by schema inspection if you have this problem - instead of 

```
  prev_pass1 varchar(255) NOT NULL default '' 
```

you will see 

```
  prev_pass1 varchar(255) NOT NULL 
```

Similarly, creating a new customer account will fail with a message like 

```
--> PHP Fatal error: 1364:Field 'customers_referral' doesn't have a default value :: INSERT INTO zen_customers 
...
```
