---
title: Additional Software 
description: Adding WordPress, Joomla, Drupal, or other software to your server
category: running
weight: 10
---

Running a blog (WordPress), a forum (phpBB, Simple Machines), a CMS (Drupal, Joomla) or a wiki (WikiMedia) on the website where you run your shopping cart is something many Zen Cart users find attractive. 

The problem is, these software packages don't maintain themselves.  You need to keep them updated or **you run the risk of being hacked**.  Even if you keep them updated, sometimes plugins are compromised by bad guys to enable sites to be hacked.  This is not just a theoretical risk - companies like Securi get most of their business from WordPress installations that have been hacked. 

So: you can do this, many people do this, but it has a cost and you'll need to devote more energy to maintenance and updates if you want go down this path. Proceed with caution.  

### Considerations: 

- Zen Cart can pass a PCI security scan done by an ASV (Approved Scanning Vendor).  Many other software packages cannot do this, so if you deploy them, you will fail a scan.  **At any time**, your payment processor can demand that you run a scan and can cut you off if you cannot prove that you have passed.  And you cannot simply go to another provider if this occurs, because they report these situations to the regulators in your jurisdiction, who can impose fines.  PCI imposes a much higher level of security requirement than the average website requires, and because you handle payments, you are subject to this requirement. 

- If you still want to blog, see [blogging](/user/running/blogging/) for alternatives to installing WordPress on your Zen Cart server. 

- If your additional software is for sending email (such as phpList), consider migrating to a paid email service provider. The FAQ on [Newsletters](/user/email/newsletters/) provides some suggestions. 

