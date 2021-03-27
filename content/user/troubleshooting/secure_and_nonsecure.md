---
title: Secure and nonsecure items 
description: Error messages "Unauthenticated content" or "connection partially encrypted" 
category: troubleshooting
weight: 10
---

### Problem:

One or more of these things happen on some or all of my "secure" pages, such as Login, My Account and Checkout.

- I am seeing a broken padlock

- When I click the Log In link as a customer i get prompted with the security prompts stating:

    "This page contains both secure and nonsecure items.
    Do you want to display the nonsecure items?"

- "Page contains unauthenticated content"

- "connection partially encrypted"



### Solution:

That indicates that somewhere in your templates or stylesheets you have hard-coded actual URL links to `http://xxxxxxxxx`,  instead of using relative paths.  See [relative URLs](/user/first_steps/relative_urls/) for more information.

This can also happen if you have added banners with `http://` links and not told them to skip display on SSL pages.

This can also happen if you have added click-tracking tools to your site via JavaScript, which link to `http://` pages somewhere.

You can identify most culprits by searching your browser's View Source for:
`src="http://`

Then work through your template files and stylesheets and remove those hard-coded links. If they are caused by click-tracking scripts somewhere, try converting them to `https://` links or contact the vendor for assistance with alternate scripts.


Basically, *never* hard-code a full `http://` URL into any page/template/stylesheet on your site unless you know for certain that doing so will not produce this sort of error.  This is especially true for 
`<img src=...>` and `<script src=...>` tags.



### ANOTHER TIP:
Sometimes these same errors are caused by images mentioned in your stylesheet. Double-check to be sure that all those images actually exist. If they don't, then they'll produce [404 Not Found](/user/troubleshooting/http_response_codes/) errors, and sometimes that'll create a "loop" to attempt displaying a 404-error-page, which can in turn throw even more messages.

And, if you have created a custom 404 page, then if *that* page has any missing images referenced on it, or on its stylesheets, you could end up in a loop that not only throws security/encryption errors, but also creates excessive traffic in your hosting account, which will make your hosting company unhappy.
