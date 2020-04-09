---
title: Mobile or Desktop - determining in your template
description: Determining your run time environment in Zen Cart 
category: template
weight: 10
---

You frequently want to do different things depending on whether your
site is being viewed in mobile or on the desktop.  

How you determine your environment will depend on the template you 
are running, and what tools are available with that template. 

The `responsive_classic` template, as well as many other templates,
builds in the [Mobile_Detect](http://mobiledetect.net/) library.  
Use this to query the environment and react accordingly. 

```
if (!class_exists('Mobile_Detect')) {
  include_once(DIR_WS_CLASSES . 'Mobile_Detect.php');
}
  $detect = new Mobile_Detect;
  $isMobile = $detect->isMobile();
  $isTablet = $detect->isTablet();
```

You likely already have a `Mobile_Detect` object built, so you can just do 

```
global $detect; // If you're in a function
if ($detect->isMobile() || $detect->isTablet()) { 
  ...
```

You might also want to check ` $_SESSION['layoutType'] == 'mobile' )`  
in case that variable is set. 

