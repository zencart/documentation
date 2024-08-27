---
title: Unknown column error after upgrade 
description: Post-upgrade blank screen when adding a record
category: Upgrading 
weight: 10
---

If you get a message like, 

``` PHP Fatal error: 1054:Unknown column 'c.customers_secret' in 'field list' ...```

or 

``` PHP Fatal error: 1054:Unknown column 'o.language_code' in 'field list' ...```

What is happening is that one or more of the `ALTER TABLE` commands in the upgrade process run by `zc_install` failed, and now a column which is expected to exist does not.

One very common root cause for this issue is a failure running an `ALTER TABLE` required by an upgrade because the table in question still has old format dates.  See the page [date standardization](/user/upgrading/date_standardization/) for instructions on how to fix this.

Errors like this are reported in [debug logs](/user/troubleshooting/debug_logs/) created by the `zc_install` process.  These special debug logs have the prefix `zcInstallLog_`.

It is less common, but still possible, that a built-in date field (such as `products_date_added`) has bad data, which causes a failed upgrade. 

**Note:** Once you fix the issue that caused the `ALTER TABLE` to fail, you will still need to run the original command to add the new field.  You may do this in phpMyAdmin or in Admin > Tools > Install SQL Patches.   Example: 

```
ALTER TABLE orders ADD language_code char(2) NOT NULL default '';
```
