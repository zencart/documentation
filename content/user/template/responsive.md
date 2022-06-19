---
title: Responsive Templates 
description: What makes a template responsive? 
category: template
weight: 10
---

Responsiveness - the ability to display properly on not just a desktop computer, but also mobile devices like phones and tablets - is a critical feature of modern templates. 

How do you know if a template is responsive? 

The easiest way would be to look at it on your smartphone.  

If you don't have a smartphone handy, or just want a quick test from your desktop web browser, you can use the mobile simulator that modern browsers generally come with.  

Here's how to do it in Google Chrome: 

1. Right click and select Inspect.

![Inspect](/images/browser_inspect.png)

2. Click the "Toggle device toolbar" icon 

![Inspect](/images/device_toolbar.png)
 
3. Now your page will display as if it were being rendered on a mobile device.  You can change the device using the dropdown at the top of the page. 

![Inspect](/images/device_dropdown.png)


Another way is just to use your mouse and grab the corner of your browser window and drag it narrower, and watch what it looks like on smaller/larger screens.

Developers and designers might appreciate the https://responsively.app tool for looking at a site by simulating various common mobile devices.

TIP: Don't design your site for "every possible mobile device." It will never be "pixel-perfect." Make it work well for the majority of devices that *your* site's visitors are using: don't worry about devices of people who aren't your target customer.

## Does Zen Cart offer a responsive template? 

Zen Cart has two free responsive templates which are well supported: 

- The [Responsive Classic template](/user/template/responsive_classic/)
- The [Bootstrap template](/user/template/bootstrap/)

## How do you achieve responsiveness? 

In order to determine how to lay out a page, the template must first determine the length and width of the visitor's screen. 

- The Responsive Classic template uses browser user-agent-detection 
- The Bootstrap template uses media queries

A deeper discussion of these topics is presented in the [Mobile or Desktop state?](/user/template/mobile_mode/) article. 
