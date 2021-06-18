---
title: Could not upgrade to version X
description: Troubleshooting a failed database upgrade
category: Upgrading 
weight: 10
---

If you get a message like, 

"Could not upgrade to version 1.5.7.  We detect that you currently have v1.5.5, and must perform the updates to get to version 1.5.6 first." 

![Could not upgrade](/images/could_not_upgrade.png)

What has happened is that the upgrade has stopped because one of the tests which ensures prior updates were done has failed.  Each database upgrade to version X will spot check whether all prior upgrades have been completed, and stop if not. 

The file `zc_install/includes/systemChecks.yml` contains the list of checks done at each version to ensure that the database has actually been up to date.  So in the case above, reviewing the 1.5.6 checks will narrow down the things to check to see what might have failed.

One very common failure is a an inability to run an ALTER TABLE because the table in question still has old format dates.  See the page [date standardization](/user/upgrading/date_standardization/) to see how to fix this.

