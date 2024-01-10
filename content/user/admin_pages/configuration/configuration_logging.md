---
title: Configuration ≫ Logging
category: admin_pages
weight: 90 
---

<h2 id="log_database_queries">Log Database Queries</h2>

<div class='indent'>Key: <b>STORE_DB_TRANSACTIONS</b><br />
Path: <b>Configuration > Logging</b><br />
Description: Record the database queries to files in the system /logs/ folder. USE WITH CAUTION. This can seriously degrade your site performance and blow out your disk space storage quotas.<br><strong>Enabling this makes your site NON-COMPLIANT with PCI DSS rules, thus invalidating any certification.</strong></div>


<h2 id="report_all_errors_admin">Report All Errors (Admin)?</h2>

<div class='indent'>Key: <b>REPORT_ALL_ERRORS_ADMIN</b><br />
Path: <b>Configuration > Logging</b><br />
Description: Do you want create debug-log files for <b>all</b> PHP errors, even warnings, that occur during your Zen Cart admin's processing?  If you want to log all PHP errors <b>except</b> duplicate-language definitions, choose <em>IgnoreDups</em>.</div>


<h2 id="report_all_errors_store">Report All Errors (Store)?</h2>

<div class='indent'>Key: <b>REPORT_ALL_ERRORS_STORE</b><br />
Path: <b>Configuration > Logging</b><br />
Description: Do you want create debug-log files for <b>all</b> PHP errors, even warnings, that occur during your Zen Cart store's processing?  If you want to log all PHP errors <b>except</b> duplicate-language definitions, choose <em>IgnoreDups</em>.<br /><br /><strong>Note:</strong> Choosing 'Yes' is not suggested for a <em>live</em> store, since it will reduce performance significantly!</div>


<h2 id="report_all_errors_backtrace_on_notice_errors">Report All Errors: Backtrace on Notice Errors?</h2>

<div class='indent'>Key: <b>REPORT_ALL_ERRORS_NOTICE_BACKTRACE</b><br />
Path: <b>Configuration > Logging</b><br />
Description: Include backtrace information on &quot;Notice&quot; errors?  These are usually isolated to the identified file and the backtrace information just fills the logs. Default (<b>No</b>).</div>


