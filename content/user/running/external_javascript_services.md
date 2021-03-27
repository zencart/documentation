---
title: Adding Google Analytics or Google Tag Manager
description: How do I install JavaScript snippets for 3rd-party tools?
category: running
weight: 10
---

## Analytics

There are many analytics services available. One popular one is Google Analytics.

These instructions apply for any vendor, not just Google. Substitute their name in the filename below.

To add VERY BASIC Google Analytics to your site, Google gives you a JavaScript code snippet to install.

The simplest way to install this basic code snippet is:

- create a new file on your server: `/includes/templates/YOURTEMPLATE/jscript/jscript_google_analytics.js`
- paste the snippet from Google in that file
- done!

(If you're putting up a snippet for a different vendor, name the file `jscript_vendorname.js` )


## Advanced e-commerce analytics

On the Zen Cart plugins library you will find some [ecommerce-specific plugins for Google Analytics](https://www.zen-cart.com/downloads.php?do=file&id=1997) 
which capture product/sale data in greater detail and transmit those to Google as part of their Analytics mining of your site.

If you install one of those plugins, you should delete the "basic" code snippet file mentioned above, else you will get conflicting data. 
Simply use one or the other, not both.


## Google Tag Manager

If you are using Google snippets for things beyond just Analytics, you can install the Google Tag Manager snippet
in the following way. Remember: this REPLACES the basic snippet file mentioned for basic analytics above.

**NOTE:** Using Tag Manager may make the use of Advanced Ecommerce Analytics impossible. Be sure to investigate for yourself.

`/includes/templates/YOURTEMPLATE/jscript/jscript_google_tag_manager.js`



