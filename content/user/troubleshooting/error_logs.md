---
title: Errorlog access  
description:  Where do I find my server's errorlog to review server-side problems?
category: troubleshooting
weight: 10
---

Your hosting company typically provides this via their control panel.

- If you use cPanel, simply log into your cPanel admin, and click on the Errorlog button.
- Other hosting systems may have the button elsewhere under their server admin tools.
- H-Sphere customers may have to enable errorlog support before it becomes available.
- Sometimes extra `errorlog` files may appear in your directories: these are usually from PHP errors that happen outside Zen Cart operation (or before Zen Cart actually begins). You can access them via FTP or your cPanel file manager.
- Some hosts don't offer it via the control panel; they may offer it via a `/logs` folder instead.  Note that this is not your Zen Cart `/logs` folder - it's above your webroot at the top of your hosting account folder. 

