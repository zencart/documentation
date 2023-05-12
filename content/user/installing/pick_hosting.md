---
title: Picking a hoster 
description: Selecting a company to host your cart 
category: installing 
weight: 10
---

As noted in [Basics - Hosting and Domain concepts](/user/first_steps/hosting/#hosting-companies): 
- Your easiest installation option will be a Linux host running Apache with cPanel.
- The decision on whether to use Shared or VPS hosting will be determined by your budget, but VPS is recommended.
- The Zen Cart project recommends a number of hosting providers on
their [Recommended Services](https://www.zen-cart.com/content.php?3-services) page.

## Red Flags
If you choose not to go with one of the Zen Cart recommended hosters, be sure to avoid hosters that do these things: 

- Hoster has a "cPanel-like" administration: some hosters use a proprietary control panel to save money on cPanel licensing fees.  These are almost always bad.  Choose a hoster that uses cPanel, not something else.
- Hoster does not support email: some hosters (notably GoDaddy) outsource their email support to other vendors (like Microsoft), which means more headaches for you in configuring and maintaing your email. 

### SSLLabs Evaluation

One way to evaluate hosts is to run the [test offered by SSLLabs](https://ssllabs.com/ssltest).  You will want to make sure any host you consider has an "A" or "A+" rating.  

   A highly rated host will help make any PCI scan you run more likely to succeed.  The more secure your host, the more secure your site.

   Here's an example of an excellent report: 

![SSL Test - A+ Grade](/images/ssltest_aplus_grade.png)

   Here's an example of a poor report: 

![SSL Test - C Grade](/images/ssltest_c_grade.png)

