---
title: Blocking Attacks 
description: How do I keep these bots away from my site? 
category: troubleshooting 
weight: 10
---


## Cloudflare

A free account on Cloudflare.com will let you manage your DNS through them, and set up IP-blocking from malicious visitors.

By default Cloudflare will then block all kinds of bad traffic automatically for you.

You can set up a firewall rule (one of five free rules available) to block a "list" of IP addresses that you manage. 
You can set up other firewall rules to block entire countries. (Be sure to only block countries you will actually never intend to sell to.)

In order for it to work, you must change your domain's Name Servers (in your domain registrar) to point to Cloudflare instead of to your hosting company.

## cpHulk
-- content coming soon 

## Config Server Firewall (CSF) 
-- content coming soon 

## Access Blocker 
If you wish to block IP addresses independently from your store's Admin (whether you also use Cloudflare or not) you might consider installing the [Access Blocker plugin](https://www.zen-cart.com/downloads.php?do=file&id=2237)


