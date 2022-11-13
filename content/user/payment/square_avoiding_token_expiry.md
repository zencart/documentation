 ---
title: Square WebPay - Avoiding Token Expiry 
description: Preventing "OAuth access token has expired" 
category: payment
weight: 10
---

## Manual Prevention 

A couple of times a week, go to Admin > Modules > Payment / Square WebPay, click **Edit** then click **Update**. 

## Automated Prevention 

Set up a [cron job](/user/first_steps/hosting/#cron) job to run at least twice a week (daily is fine too) that refreshes the token.  

Depending on your server configuration, you can do 

```
php PATH_TO_STORE/squareWebPay_handler.php
```

(where PATH_TO_STORE is the value of `DIR_FS_CATALOG` from your `includes/configure.php` file)

or 

```
/usr/bin/wget https://YOURSTORE/squareWebPay_handler.php
```
