---
title: Mobile or Desktop - determining in your template
description: Determining your run time environment in Zen Cart 
category: template
weight: 10
---

Responsiveness - the ability to display properly on not just a desktop computer, but also mobile devices like phones and tablets - is a critical feature of modern templates. 

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

Another approach is the one used by [Twitter Bootstrap](https://getbootstrap.com/).   Bootstrap uses Javascript to determine the appropriate presentation for the device in use.  Bootstrap proponents argue that bootstrap is faster 
to load and more well maintained than Mobile Detect.

<!-- FIXME - build out this explanation --> 

Another approach is **not to use** any offsite scripting or mobile detection script at all!  

There is a movement in responsive design that requires some forward thinking in coding.  Using tables for true spreadsheet style lists only and nesting DIV tags and CSS for responsive designs.  By thinking of div tags as containers in layout designs you can create a responsive layout without using any scripting.  

The desire to support different screens are even pushing a change in browsers and demanding a change in HTML. With Cascading Style Sheets CSS3 which is growing in versions so fast that version numbers are no longer used.

