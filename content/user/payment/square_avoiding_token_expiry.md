 ---
title: Square - Avoiding Token Expiry 
description: Preventing "OAuth access token has expired" 
category: payment
weight: 10
---

## Manual Prevention 

A couple of times a week, go to Admin > Modules > Payment / Square WebPay, click **Edit** then click **Update**. 

## Automated Prevention 

Set up a [cron job](/user/first_steps/hosting/#cron) job to run twice a week that does 

```
/usr/bin/wget https://YOURSTORE/squareWebPay_handler.php
```
