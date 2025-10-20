---
title: Fabricating Email Addresses 
description: Creating email addresses for customers who don't have them
category: email
weight: 10
---

If you have customers who want to buy online from you but don't have an email address, the solution is straightforward: as suggested in [login as customer](/user/running/login_as_customer/), you can simply create an email using their name.  For example, if your customer's name was Scott Wilson, you could create an account with the email scott.wilson@YOURDOMAIN.com.

There is just one problem: if the email address scott.wilson@YOURDOMAIN.com doesn't exist, the email will bounce, and too many bounces will cause your hoster to complain and/or your deliverability to suffer. 

There are a couple of solutions to this issue: 

a) Depending on how your email is configured, your email server may have the option of a "catch all" email.  Non-existent emails will be forwarded to this address and thus not bounce. 

b) You can modify the Zen Cart software to not send to non-existent addresses. Here's a sample implementation from Zen Cart 1.5.7: 

In `includes/functions/functions_email.php`, right before the check of `EMAIL_MODULES_TO_SKIP`, i.e. 

```
    if (defined('EMAIL_MODULES_TO_SKIP') && in_array($module,explode(",",constant('EMAIL_MODULES_TO_SKIP')))) return false;
```

add code that checks a defined constant (`LIVE_EMAIL`) containing valid addresses at your domain.  Skip sending if the email has your domain name but is not in this list. 

```
    $mail_parts = explode('@',strtolower($to_address)); 
    if ($mail_parts[1] == 'YOURDOMAIN.com') {
       $good_emails = explode(",", LIVE_EMAIL);
       if (empty($good_emails)) return; 
       for ($i = 0; $i < sizeof($good_emails); $i++) {
          $good_emails[$i] = trim($good_emails[$i]); 
          $good_emails[$i] = str_replace('@YOURDOMAIN.com','',$good_emails[$i]); 
       }
       if (in_array($mail_parts[0], $good_emails)) {
         // continue processing 
       } else {
          return true;  // pretend we have sent the email
       }
    } 
```

The constant `LIVE_EMAIL` would be created in Admin > Tools > Install SQL Patches like this: 

```
INSERT INTO configuration (configuration_title, configuration_key, configuration_value, configuration_description, configuration_group_id, sort_order, last_modified, date_added, use_function, set_function) VALUES ('Known Good Emails', 'LIVE_EMAIL', '', 'Comma separated list of good emails at YOURDOMAIN.com', 12, 125, NULL, now(), NULL, NULL);
```

and then accessed in Admin > Configuration > Email Options.

