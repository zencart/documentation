---
title:  Caching 
description: Why doesn't my new image show?
category: new_user_topics
weight: 10
aliases:
    - /user/new_user_topics/caching/
---

"Why don't I see my new image?"

"Why don't I see my new CSS style?" 

"Where's my JavaScript function update?" 

[Image Caching](/user/new_user_topics/change_header_logo/#image-caching) is one form of caching, but many other things can also be cached, meaning you won't see your changes right away. 

If you upload a new file with the same name as an existing file, in many cases you won't see the change right away in your browser.  This could be for an image, a CSS file or a JavaScript file.  Why is this? 

It's because of a browser behavior called _caching_.  

The reason for this is that the default configuration of browsers (and Zen Cart) is to assume that you are a _user_, not a _developer_, so it tries to make your browsing experience faster by caching images.  Caching an image means retrieving it one time from the webserver to your local computer, and then using the local copy next time the image is needed, thereby saving the time required to retrieve it.

**You can clear the cached version of the current page by doing a hard refresh:**

- On Windows, use  **Ctrl+Shift+R** 
- On Mac, use **Cmd+Shift+R** (or **Cmd+Option+R** on Safari)
- On most computers, hold **SHIFT** while clicking the Reload Icon with the mouse

For images, you can also right click on the image, select "Open Image in New Tab",  and do a hard refresh there. 


### Disabling Browser Cache

Since you are acting as a developer while you work on your site, you may want to turn caching off.  The way this is done is specific to every browser and environment, so you'll have to do a web search to figure out how to do it with the tools you are working with.  

_The easiest way_ to get this working the first time is to use Google Chrome on a desktop computer, and follow these steps: 

- Right click and select Inspect. 

	![Inspect](/images/browser_inspect.png)

- Click the Network Tab

	![Network](/images/browser_network.png)

- Check the box that says Disable Cache

	![disable_cache](/images/browser_disable_cache.png)

- With the Inspect window open, refresh the page being tested.

Once you have mastered this technique, you can figure out how to do it in other browsers and environments.  _It is particularly tedious to do this on a mobile device_, so use a desktop computer until you have more experience doing this sort of thing. 

## Other Causes of Caching 

There are other kinds of caching which can be set up server-side that you might need to check or disable during development, or your changes won't be immediately visible.  For example, 

- Some hosters (notably SiteGround) run a utility called Dynamic Cache
- CloudFlare has built-in caching 
- Some sites running Securi and/or WordPress have caching 
- [FPM](/user/running/fpm) based servers often cache pages

