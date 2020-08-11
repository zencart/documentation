---
title: SSL certificate - yes you need one 
description: You need an SSL certificate to run Zen Cart
category: first_steps 
weight: 10
---

If you understand that you need an SSL certificate, you can skip this article.

Many storeowners are uncertain whether they should add SSL to their site, citing various reasons, including cost and complexity of setup.  

**MODERN ANSWER: Yes, you should use SSL on your site. Not only does it lend to protecting sensitive information, but it is also becoming more and more important for good search engine ranking nowadays.**  

Now for the technical and bigger-picture explanation:  

Here are the things to consider:  

**WHY USE SSL?**  

SSL encrypts communications between your customer's browser and your webserver. This means nobody can snoop on what they're transmitting to you (such as someone spying on internet traffic in a cafe or wifi hotspot, or library)  

**DO I NEED SSL?**  

Yes, you need SSL. 

Years ago, there was a line of thinking that if your site did payment collection offsite (e.g. PayPal Standard), you didn't really need SSL.  

Even back then, this was bad advice.  

Here's why: without an SSL certificate, traffic to and from your website transits the Internet in clear plain text.  So anyone who's watching can see what's being sent. 

- Without an SSL certificate, your admin credentials are transmitted in plain text, meaning anyone can see them and get access to your admin panel. 
- Without an SSL certificate, your customer's personal information and purchase data are transmitted in plain text, meaning anyone who's watching can record these details. 

Finally, SSL is considered a ranking factor by Google, and many browsers
now warn customers not to purchase from sites that don't have SSL. 

See that ugly warning? 

**Don't let this be you!**

<img src="/images/insecure_cart.png" alt="Insecure cart" width="50%" />

**HOW DOES ZEN CART IMPLEMENT MY SSL?**  

Arrange an SSL certificate with your hosting company, and then update your `configure.php` files to use your SSL address (the one starting with `https` rather than `http`). 

`includes/configure.php`: update your `HTTP_SERVER` and `HTTPS_SERVER` defines. 

`admin/includes/configure.php`:  update your `HTTP_SERVER`, `HTTP_CATALOG_SERVER` and `HTTPS_CATALOG_SERVER` defines.  If it exists, update your `HTTPS_SERVER` define.

You want your *whole site* to be running SSL.  

**HOW DO I INSTALL A CERTIFICATE?**

Installing an SSL certificate is a subject specific to your hosting account. Work with your hosting company or follow their FAQ documentation to buy and install an SSL certificate in your hosting account.  

Then make sure you can visit your site using your SSL URL without getting server errors.  

And then you can tell Zen Cart to use your new SSL URL. See the FAQ below for that part.  

### Further Related Reading:  

- [How do I enable SSL?](/user/installing/enable_ssl/)

- [What is an SSL certificate?](/user/security/ssl_cert/) 
