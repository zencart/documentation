---
title: How Zen Cart uses cookies 
description: Cookies and Session data 
category: security
weight: 10
---

A fresh clean _uncustomized_ installation of Zen Cart does VERY LITTLE with cookies or anything related to "tracking" of visitors.  

### COOKIES  
Zen Cart requires that the visitor's computer accept a session cookie. This session cookie contains simply the session ID number which identifies the visitor to the store, as separate from other visitors. The session cookie contains no personal identity information, and in itself is thus anonymous as a 3rd-party cannot use anything in the cookie to identify the visitor in any way.  
In a traditional configuration, and by definition, this session cookie expires at the end of the visitor's session in the browser, or at a predefined time (typically 24 minutes) after their last "click", whichever is sooner.  

### SESSIONS  
The session ID is used only to recognize what the visitor has done during their visit to the store. This includes things like: whether the visitor has put something in their shopping basket, whether they have logged in, and allows them to proceed through checkout.  

### EXCEPTIONS  
Storeowners who alter the original Zen Cart code by the use of addons/plugins, custom code, additional HTML in templates, adding JavaScript segments, etc, may be engaging in additional tracking and using additional cookies for broader purposes than Zen Cart itself requires. Each store's configuration and activity is unique to their own implementation. Each storeowner is responsible for their own use of the software and the addons/plugins/external-code and any other alteration they make to it.  

### DISCLAIMER  
This article is for general informational purposes only. It is NOT legal advice, nor should it be relied upon as such. This information is not intended to replace proper legal counsel. Zen Ventures, LLC assumes no liability or responsibility for the use of this information, nor for ways in which any shop has altered the use or function of Zen Cart official code. It is up to individual storeowners to disclose the ways in which their store operates differently from core basic Zen Cart functionality.

