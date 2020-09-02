---
title: Mobile or Desktop state? - determining in your template
description: Determining your visitor's device in Responsive Classic
category: template
weight: 10
---

[Responsiveness](/user/template/responsive/) - the ability to display properly on not just a desktop computer, but also mobile devices like phones and tablets - is a critical feature of modern templates. 

Determining the kind of device being used can be done in different ways.  How you do it will depend on the template you are running, and what tools are available with that template. 

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

You might also want to check ` $_SESSION['layoutType'] == 'mobile'` in case that variable is set. 

Another approach is the one used by [Twitter Bootstrap](https://getbootstrap.com/).   Bootstrap uses Javascript to determine the appropriate presentation for the device in use.  Bootstrap proponents argue that bootstrap is faster to load and more well maintained than Mobile Detect.  You can observe how this is done in the Zen Cart admin, which makes heavy use of Bootstrap. 

Yet another approach is **not to use** any offsite scripting or mobile detection script at all.  This school of responsive web design emphasizes using tables only for true spreadsheet style lists, and nesting DIV tags and CSS. 

