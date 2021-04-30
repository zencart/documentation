---
title: EZ-Page Not Found
description: When I go to my EZ-Page, it says the page you were attempting to access cannot be found
category: ezpages
weight: 10
---

If you have hard coded a link to an EZ-Page, but when you click it you get a message at the top of the screen saying 

> Sorry, the page you were attempting to access cannot be found.

there are a few possible root causes: 

- The specified page literally does not exist.  If your URL is `YOURSITE.com/index.php?main_page=page&id=310`, but when you go to Admin > Tools > EZ-Pages, you don't see EZ-Page id 301, you will get the page not found error.  Update your link to refer to an existing EZ-Page.

- The specified page does exist, but is not visible (has Page is Visible = 0 and 0 values for all Order fields). See "Setting Visibility" in [Admin Interface to EZ-Pages](/user/admin_pages/tools/ezpages/) to learn how to update these values. 

