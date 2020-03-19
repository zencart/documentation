---
title: Configuration-Logging
category: admin_pages
weight: 90
---

<b>Log Database Queries</b>

<div class='indent'>Record the database queries to files in the system /logs/ folder. USE WITH CAUTION. This can seriously degrade your site performance and blow out your disk space storage quotas.<br><strong>Enabling this makes your site NON-COMPLIANT with PCI DSS rules, thus invalidating any certification.</strong></div>


<b>Report All Errors (Admin)?</b>

<div class='indent'>Do you want create debug-log files for <b>all</b> PHP errors, even warnings, that occur during your Zen Cart admin's processing?  If you want to log all PHP errors <b>except</b> duplicate-language definitions, choose <em>IgnoreDups</em>.</div>


<b>Report All Errors (Store)?</b>

<div class='indent'>Do you want create debug-log files for <b>all</b> PHP errors, even warnings, that occur during your Zen Cart store's processing?  If you want to log all PHP errors <b>except</b> duplicate-language definitions, choose <em>IgnoreDups</em>.<br /><br /><strong>Note:</strong> Choosing 'Yes' is not suggested for a <em>live</em> store, since it will reduce performance significantly!</div>


<b>Report All Errors: Backtrace on Notice Errors?</b>

<div class='indent'>Include backtrace information on &quot;Notice&quot; errors?  These are usually isolated to the identified file and the backtrace information just fills the logs. Default (<b>No</b>).</div>


