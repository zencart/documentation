---
title: Buttons 
description: How to customize buttons 
category: template
weight: 10
---

Most recent Zen Cart installations use the **CSS Buttons** feature of Zen Cart, which is enabled in [Admin > Configuration > Layout Settings](/user/admin_pages/configuration/configuration_layoutsettings/).

![CSS Button](/images/button_css.png)

No action is required to create a CSS button; it simply uses the button text and displays it according to the styling your template has set. 

Prior to the introduction of the CSS buttons feature in 1.3.0, Zen Cart buttons were static .gif images like the one shown below: 

![GIF button](/images/button_gif.png)

Many of them were much smaller - just enough space to fit the text describing their action. 

<img src="/images/button_add_selected.gif" alt="GIF button - add selected" style="border-style: none !important" />

You are free to use either setting, but most people prefer the maintenance free and more modern looking CSS buttons.  

If you decide you want to use static images and customize them, you'll want to build a full set - do each of the filenames in `includes/templates/template_default/buttons/english/`.  There are currently 52 of them. 

