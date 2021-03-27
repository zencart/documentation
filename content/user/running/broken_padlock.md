---
title: Broken Padlock 
description: Why does my site show as insecure? 
category: Running
weight: 10
---

A _broken padlock_ is what you get when your website is not fully secured. 
It's called a "broken padlock" because browsers used to show an image of a broken padlock in the address bar. 

![Firefox Insecure Cart](/images/ff_broken_padlock.png) 


Some browsers will simply display a message saying "Not Secure" like this: 

![Insecure Cart](/images/insecure_cart.png) 


## Common Causes of broken padlock. 

#### Mixed Content 

Mixed content means although the page is being referenced using SSL (i.e. it starts with `https://`), some of the internal references are non-SSL.  Generally this indicates that you are loading images, fonts, CSS or JavaScript over `http` rather than `https`. 

If you see a "Not Secure" message, but click on the message and see a valid certificate, the problem might be caused by mixed content.

![Insecure Cart](/images/not_secure_mixed.png) 


If you do a "View Source" in your browser and search for "http://" you can often find the root cause quickly.  If you need more help, the [find http references](https://www.zen-cart.com/downloads.php?do=file&id=2197) plugin builds a report on issues like this.  

#### Expired SSL Certificate

SSL certificates must be renewed, and you forget to renew (or the credit card you use to auto-renew is expired). You'll get a broken padlock.  

Clicking on the message will show a dialog like this: 

![Insecure Cart - invalid cert](/images/not_secure_invalid.png) 

Clicking on the Certificate line will show a dialog like this: 

![Insecure Cart](/images/expired_certificate.png) 

