---
title: Mobile or Desktop state? 
description: Determining your visitor's screen size 
category: template
weight: 10
---

[Responsiveness](/user/template/responsive/) - the ability to display properly on not just a desktop computer, but also mobile devices like phones and tablets - is a critical feature of modern templates. 

Determining the kind of device being used can be done in different ways.  How you do it will depend on the template you are running, and what tools are available with that template. 

The `responsive_classic` template 
uses the [Mobile_Detect](http://mobiledetect.net/) library to 
determine the screen characteristics. 

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

You might also want to check ` $_SESSION['layoutType'] == 'mobile'` in case that variable is set. 

* * *

Another approach is the one used by [Twitter Bootstrap](https://getbootstrap.com/). Bootstrap uses the CSS "media queries" breakpoints feature to determine the appropriate presentation for the device in use.  Bootstrap proponents argue that bootstrap is faster to load and more well maintained than Mobile-Detect. You can observe how this is done in the Zen Cart admin, which makes heavy use of Bootstrap.

