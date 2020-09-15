---
title: max_user_connections exceeded
description: Seeing max_user_connections errors in logs
category: troubleshooting 
weight: 10
---

The "max_user_connections exceeded" message typically only happens when you're getting a flood of simultaneous connections to your site.

Visitors hitting your site and triggering that error would have seen a blank page. (or whatever a [500-error](/user/troubleshooting/http_response_codes/) page looks like for your server).

Most web applications like Zen Cart use only a single MySQL "user" to connect to the database, and most hosts configure max_user_connections to be big enough to handle typical traffic load. Traffic load includes all visits at any given second, including "you", your customers, your visitors-who-are-not-yet-customers, search engine bots, and anybody trying bad things on your site.

Possible causes:

- Sending an email promotion and everyone opens the email and clicks on a link to your site from inside that email "all at the same time", causing a "flood" of simultaneous traffic larger than the max_user_connections setting

- Disobedient Search Engine spiders/crawlers. Normally bots crawl at a slow enough pace to not overload your site. Obedient crawlers will read a robots.txt file you can place on your site to tell each search engine what rules you want them to follow, such as how much time to wait between hits. Only the good crawlers will obey these rules, so it's not a magic fix for bad actors.

Things to check:

- The IP address in the log can be used to lookup where it comes from in a Whois database. Knowing this may give you clues about the authenticity of whatever they were attempting to do.
If the problem is chronic, you might consider IP blocking, because there's no good reason for the same IP to be making multiple simultaneous hits that floods your server. But, be careful: a legit customer could come along while a bad flood has overloaded things and the legit customer would show up in the log, so you don't want to block the wrong person!

Options:

- If you think there's enough demand for more legit traffic, you could ask whether your hosting company will increase the max_user_connections setting to something higher.
- You could block IP addresses of bad traffic after inspecting each IP in the logs to be sure it makes sense to block them.
- You could configure the robots.txt file to tell bots to crawl more slowly - http://www.robotstxt.org
