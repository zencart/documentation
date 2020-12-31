---
title: SSL certificate - yes you need one 
description: Why your online store should be using SSL / HTTPS
category: first_steps 
weight: 10
---

Using HTTPS for secure communication is the norm, and expected, on all websites -- especially those engaged in e-commerce.

If you understand that you need to use HTTPS and already have an SSL certificate, you can skip this article.

If you're not sure what an SSL certificate is, please review [what is an SSL certificate](/user/security/ssl_cert/) first.

<hr>

Many storeowners are uncertain whether they should use HTTPS (add SSL to their site), citing various reasons, including cost and complexity of setup.  

**MODERN ANSWER: Yes, you should use SSL on your site. Not only does it lend to protecting sensitive information, it is also important for good search engine ranking nowadays.**  

Now for the technical and bigger-picture explanation:  

Here are the things to consider:  

**WHY USE SSL?**

SSL encrypts communications between your customer's browser and your webserver. This means nobody can snoop on what they're transmitting to you (such as someone spying on internet traffic in a cafe or wifi hotspot, or library)  

**DO I NEED SSL?**  

Yes, you need SSL. 

Years ago, there was a line of thinking that if your site did payment collection offsite (e.g. PayPal Standard), you didn't really need SSL.  

Even back then, this was bad advice.  

Here's why: without using HTTPS (SSL), traffic to and from your website transmits over the Internet in clear plain text.  So, anyone who's watching can see what's being sent. 

- Without an SSL certificate, your admin credentials are transmitted in plain text, meaning anyone can see them and get access to your admin panel. 
- Without an SSL certificate, your customer's personal information and purchase data are transmitted in plain text, meaning anyone who is watching can record these details. 

Finally, SSL is considered a ranking factor by Google. And, many browsers now warn customers not to purchase from sites that don't use SSL / HTTPS. 

See that ugly warning? 

**Don't let this be you!**

![Insecure Cart](/images/insecure_cart.png)

**HOW DOES ZEN CART IMPLEMENT MY SSL?**  

Arrange for an SSL certificate with your hosting company, and then update your `configure.php` files to use your SSL URL address (the one starting with `https` rather than `http`) for the value (second parameter, the URL) of each of these defines:

`includes/configure.php`: update your `HTTP_SERVER` and `HTTPS_SERVER` defines. 

`admin/includes/configure.php`:  update your `HTTP_SERVER`, `HTTP_CATALOG_SERVER` and `HTTPS_CATALOG_SERVER` defines.  If it exists, update your `HTTPS_SERVER` define.

For example, if you have 

```
define('HTTP_SERVER','http://mysite.com'); 
```

change this to 

```
define('HTTP_SERVER','https://mysite.com'); 
```

Change all these defines, even the ones that start with `HTTP_`.  Why?  Because you want your *whole site* to be running SSL.  

**HOW DO I INSTALL A CERTIFICATE?**

Installing an SSL certificate is a subject specific to your hosting account. Work with your hosting company or follow their FAQ documentation to buy and install an SSL certificate in your hosting account.  Many hosts will provide a free SSL certificate with certain hosting plans.

Then make sure you can visit your site using your SSL URL without getting server errors.  

And then you can tell Zen Cart to use your new SSL URL. See the defines above, or consult the FAQs below for that part.  

### Further Related Reading:  

- [How do I enable SSL?](/user/installing/enable_ssl/)

- [What is an SSL certificate?](/user/security/ssl_cert/) 
