---
title: Bootstrap Template for Zen Cart
description: What is the Bootstrap Template? 
category: template
weight: 10
---

Developers: please see [developer information on Bootstrap](/dev/libraries/bootstrap/) for technical details.

The [Bootstrap template](https://www.zen-cart.com/downloads.php?do=file&id=2191) is a well supported, standards-based, [responsive](/user/template/responsive/) template which was built by the Zen Cart community. 

The Bootstrap template is built on the [Bootstrap](https://getbootstrap.com/) front-end toolkit.  It differs from - **and is better than** - the older [Responsive Classic](/user/template/responsive_classic/) template in the following ways: 

||Bootstrap|Responsive Classic| 
-|-|-|
|Determining screen size|CSS Media Queries | [Mobile_Detect](http://mobiledetect.net/) library |
|CSS|Single CSS file|Separate CSS for desktop, tablet and phone|
|Orientation Handling|Built in|Requires different CSS for landscape vs portrait on mobile devices|
|Device Support|Device independent|Lists specific devices|

Again, each of these points of difference is actually an advantage for Bootstrap; the way it does things is more modern and suited to a mobile-first world.  Note further that the disadvantages of Responsive Classic are also present in the older Picaflor Azul Responsive templates and most templates from stores like ThemeForest.  **The Bootstrap Template is really your best option.** 

Bootstrap template version 3.X is based on [Bootstrap 4](https://getbootstrap.com/docs/4.6/getting-started/introduction/).  You can find the exact version of Bootstrap (`major.minor.patch`) in use by looking at the file `includes/templates/bootstrap/common/html_header.php`, which pulls in the Bootstrap javascript and css.

### Bootstrap Template - Product Page (Desktop) 
![Bootstrap Template Product Page on Desktop](/images/bootstrap_desktop.png)

### Bootstrap Template - Product Page (Mobile) 
![Bootstrap Template Product Page on Mobile](/images/bootstrap_full.png)

### Colors in the Bootstrap Template

One of the best things about the Bootstrap template is that it puts the control of colors in the hands of the storeowner.  Using Admin > Tools > ZCA Bootstrap Colors, you can set many of the colors in your template. 

![Bootstrap Colors](/images/bootstrap_colors.png)

Some documentation on the colors is provided in the [template's Wiki](https://github.com/lat9/ZCA-Bootstrap-Template/wiki/ZCA-Bootstrap-Stylesheets-and-Colors).

### Icons in the Bootstrap Template 

The Bootstrap template uses [FontAwesome](/user/template/font_awesome/).  Technical details on versions are provided in [Font Awesome in Zen Cart](/dev/libraries/font_awesome/). 

### Plugins for the Bootstrap Template 

- [Flexible Footer for Bootstrap](https://www.zen-cart.com/downloads.php?do=file&id=2397) - adds a multi-column footer to the Bootstrap template.
