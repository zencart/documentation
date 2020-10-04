---
title: Template Images 
description: What directories contain all the template images? (i.e. buttons, icons, images etc.)?
category: template
weight: 10
---

Note that by default, YOURLANGUAGE is "english" and YOURTEMPLATE is "responsive_classic". 

<p class="ZenBody"><span style="color: maroon;">/images</span> folder: This is where your Product images are located.</p>

<p class="ZenBody"><span style="color: maroon;">/includes/languages/YOURLANGUAGE/images</span> folder: <span style="color: blue;">icon.gif</span> (your language flag).</p>

<p class="ZenBody"><span style="color: maroon;">/includes/templates/YOURTEMPLATE/buttons/YOURLANGUAGE</span> folder: contains the buttons used by the cart.</p>

<p class="ZenBody"><span style="color: maroon;">/includes/templates/YOURTEMPLATE/images</span> folder: contains <span style="color: blue;">header_bg.jpg</span>, <span style="color: blue;">logo.gif</span> and other images required by your template files.</p>

<p class="ZenBody"><span style="color: maroon;">/includes/templates/YOURTEMPLATE/images/icons</span> folder: contains additional images used by the cart (specific to your template)</p>

<p class="ZenBody"><strong style="">NOTE:</strong> if your template is looking for an image in the <span style="color: maroon;">/includes/templates/YOURTEMPLATE/images</span> folder but cannot find it, Zen Cart will use the image in the <span style="color: maroon;">/includes/templates/template_default/images</span> folder.</p>
