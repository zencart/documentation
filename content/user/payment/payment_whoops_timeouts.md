---
title: Whoops timeouts after payment 
description: Error when you return to your cart after offsite payment
category: payment
weight: 10
---

Situation: You are getting the message "Whoops! Your Session has Expired" after completing offsite payment. 

This is a result of the samesite cookie rule that modern browsers are enforcing.  If you want to force browsers into lower-security mode by disabling the samesite cookie rules they're programmed to follow, then you can do the following:

Create a file named `includes/extra_configures/samesite_cookie.php` containing the following:

```
<?php
// -----
// Samesite cookie needs to be 'none' when doing offsite payment gateway redirects
//
define('COOKIE_SAMESITE', 'none');
```

