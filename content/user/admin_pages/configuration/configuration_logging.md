---
title: Configuration > Logging
category: admin_pages
weight: 90 
---

<h2 id="log_page_parse_time">Log Page Parse Time</h2>

<div class='indent'>Key: <b>STORE_PAGE_PARSE_TIME</b><br />
Description: Record (to a log file) the time it takes to parse a page</div>


<h2 id="log_destination">Log Destination</h2>

<div class='indent'>Key: <b>STORE_PAGE_PARSE_TIME_LOG</b><br />
Description: Directory and filename of the page parse time log</div>


<h2 id="log_date_format">Log Date Format</h2>

<div class='indent'>Key: <b>STORE_PARSE_DATE_TIME_FORMAT</b><br />
Description: The date format</div>


<h2 id="display_the_page_parse_time">Display The Page Parse Time</h2>

<div class='indent'>Key: <b>DISPLAY_PAGE_PARSE_TIME</b><br />
Description: Display the page parse time on the bottom of each page<br />(Note: This DISPLAYS them. You do NOT need to LOG them to merely display them on your site.)</div>


<h2 id="log_database_queries">Log Database Queries</h2>

<div class='indent'>Key: <b>STORE_DB_TRANSACTIONS</b><br />
Description: Record the database queries to files in the system /logs/ folder. USE WITH CAUTION. This can seriously degrade your site performance and blow out your disk space storage quotas.<br><strong>Enabling this makes your site NON-COMPLIANT with PCI DSS rules, thus invalidating any certification.</strong></div>


