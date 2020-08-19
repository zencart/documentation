---
title: Logo Image Caching 
description: How to prevent Logo displaying improperly due to caching
category: new_user_topics
weight: 10
---

The reason the instructions mention changing the name of the logo image is to ensure that the old logo isn't cached.  

If you simply replace `includes/templates/YOURTEMPLATE/images/logo.gif` with your own logo using the same name, your browser will likely not pick up the change.  The reason for this is that the default configuration of browsers is to assume that you are a _user_, not a _developer_, so it tries to make your browsing experience faster by caching images.  Caching an image means retrieving it one time from the webserver to your local computer, and then using the local copy next time the image is needed, thereby saving the time required to retrieve it.

You can eliminate the problem by doing a hard refresh (Win Ctrl+Shift+R or Mac+Cmd+Shift+R) or right clicking on the image to show the image in a new browser page and then doing a hard refresh. But since you are acting as a developer while you work on your site, you may want to turn this behavior off.  The way this is done is specific to every browser and environment, so you'll have to do a web search to figure out how to do it with the tools you are working with.  

_The easiest way_ to get this working the first time is to use Google Chrome on a desktop computer, and follow these steps: 

- Right click and select Inspect. 

	![Inspect](/images/browser_inspect.png)

- Click the Network Tab

	![Network](/images/browser_network.png)

- Check the box that says Disable Cache

	![disable_cache](/images/browser_disable_cache.png)

- With the Inspect window open, refresh the page being tested.

Once you have mastered this technique, you can figure out how to do it in other browsers and environments.  _It is particularly tedious to do this on a mobile device_, so I recommend using a desktop computer until you have more experience doing this sort of thing. 