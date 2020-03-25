---
title: SSL certficate - yes you need one 
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
If your site is collecting credit card info directly in a page inside your store (ie: not redirecting to a bank or payment gateway site to collect card info for payment) then YES you absolutely MUST use SSL to protect your customers' payment information.  

However, the best practice now is for all sites to run SSL all the time, 
whether or not they are handling payment data. 

**HOW DOES ZEN CART IMPLEMENT MY SSL?**  
If you have SSL enabled in your hosting account (that's something you arrange with your hosting company directly), then you can tell Zen Cart to use your SSL URL, and then Zen Cart will automatically use that SSL URL when presenting pages dealing with sensitive information like login, account-creation, password changes, checkout, and even your admin pages.  

The modern way to use SSL is to have your entire site run as SSL, so the 
`HTTP_SERVER` and `HTTPS_SERVER` both use the `https` URL.  In the past,
the `HTTP_SERVER` would serve pages over `http`, using the rationale that 
these pages don't deal with sensitive information (such as a customer browsing your available products).  This is no longer considered a good practice.

**BUT MY PAYMENTS HAPPEN OFFSITE.**  
If your payment-collection is ALWAYS handled offsite via another gateway that uses SSL on its site, then *your* site does not "technically" require SSL insomuch as it's not handling credit card details. 

But if you don't have SSL enabled on your site then some spy could still steal your customers' passwords and names and addresses and email addresses when they fill in various fields on your store's site. They could then use that information to login to their accounts and impersonate them. While they couldn't make purchases using their private banking/creditcard data (since ZC doesn't store any banking/card data), they could request a cancellation of an order, or initiate communications with you under the customer's name while not actually being the customer, etc.  

Adding SSL to your site prevents the ability for such identity theft.  

**HOW DO I INSTALL A CERTIFICATE?**
Installing an SSL certificate is a subject specific to your hosting account. Work with your hosting company or follow their FAQ documentation to buy and install an SSL certificate in your hosting account.  

Then make sure you can visit your site using your SSL URL without getting server errors.  

And then you can tell Zen Cart to use your new SSL URL. See the FAQ below for that part.  

Further Related Reading:  
- [How do I enable SSL?](/user/installing/enable_ssl/)

- [What is an SSL certificate?](/user/security/ssl_cert/) 
