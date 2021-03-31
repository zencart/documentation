---
title: JavaScript Libraries 
description: Keeping your JavaScript libraries current 
category: Upgrading
weight: 10 
---

Most modern templates, as well as the Zen Cart admin, bundle in the JavaScript library `jQuery`, as well as other JavaScript libraries. 

You must check the versions of any libraries you are importing to ensure that you are running the latest, and not an older version with known vulnerabilities.

Your template's `html_header.php` or `jscript/jscript_xxxxxxx.*` files are common places to check for direct references to old libraries.  You will also want to check the `includes/templates/YOURTEMPLATE/jscript` folder to see if there are old versions stored there. 

Remember that addons to templates often bring in their own jQuery version that is likely older than the one you want to use for your template. Make sure you're only loading **one** copy of jQuery, and that the copy you are loading is current and compatible with all the other JavaScript and/or jQuery features you're already using.

A very easy way to test whether your libraries are current is to use Google Lighthouse utility.  In Google Chrome, right click and select "Inspect." 

![Inspect](/images/browser_inspect.png)

Then in the dialog that comes up, on the right side, click "Lighthouse."

![Lighthouse](/images/lighthouse.png)

Click the Generate Report button, and look under "Best Practices."  The message in this screenshot indicates that the Bootstrap and jQuery libraries need to be updated. 

![Lighthouse error](/images/best_practices.png)

