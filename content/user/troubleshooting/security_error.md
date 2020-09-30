---
title: There was a security error when trying to login
description: Sorting out expired or invalid form submissions
category: troubleshooting
weight: 10
---

**Situation:**

I'm getting this error when trying to login from the customer screen "There was a security error when trying to login"

**Cause:**

Zen Cart has a security feature to prevent spoofed external logins. A "security token" field must exist on all login forms, actually on all forms submitting data via POST. This token must be current (not expired), and must be submitted with the rest of the form data; in the case of login, that would be the login username+password in order for logins to work properly.

**Remedy:**

First, if this is happening on a page that has been sitting at a login prompt for longer than about 20 minutes, it could be that the security token has expired in the background. Refreshing the page fixes that, and so does getting the login failure (ie: after the login failure the token is refreshed and the next login will work fine).

If it is happening *all the time* and not just once in awhile, then it could be a coding issue with your template or customizations you've made to your site or with plugins you've installed (or maybe you upgraded from an older version that didn't have the security protections):

- All your forms, both admin and non-admin, need to use `zen_draw_form()` instead of hard-coding a `<form>` tag.

- Additionally, if you have customized your `/includes/functions/sessions.php` file for some reason, you'll also need to merge the new changes for this core file into your customized version.

Other Considerations:
If you're seeing this problem,  then one of the following may be the root cause:

- old obsolete template files, as explained above
- your browser is unable to set session cookies, or you're using Private Browsing mode or Incognito mode. 
- you've set your site up on an IP address instead of a domain name, thus preventing session cookies from being set properly
- your PHP configuration can't negotiate sessions properly.  Your server's PHP configuration has `session.use_only_cookies` set to `1`. It needs to be `0`. Have your hosting company fix it.
- if it only happens for a page you've bookmarked, then maybe your browser's bookmark is bad and needs to be deleted and recreated
