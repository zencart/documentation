---
title: Error 2006 MySQL server has gone away or 2013 Lost connection to MySQL server during query
description:  What do I do with this message? 
category: troubleshooting
weight: 10
---

"MySQL server has gone away" means that when you clicked on something to ask Zen Cart to do something, it started processing the request, but when it went to retrieve data from the database, it found that the database connection had disconnected, but not by Zen Cart's request.

Possible causes: 

- slow connection to external systems being accessed to produce part of page contents (e.g.: a USPS shipping quote when USPS servers are running slow)
- your own webserver is running slow (perhaps due to bogged down processing while the server is handling a bunch of spam email, or if your server is overloaded because your hosting company has too many customers on the one server)
- your hosting company may have configured the server to expire database connections on a very short time period. Most hosts allow connections to remain open for 30 seconds or more, depending on how they have other systems such as PHP configured.

You should be asking your hosting company what's changed on the server, if anything, and reporting to them that you're experiencing database disconnections (connections dropping) that you weren't seeing earlier.

They will want to know what *you* have changed, as well.

