---
title: The Developer's Toolkit
description: Searching your cart files using the admin 
category: admin
weight: 10
---

Say, for example, you wish to change the welcome email text because you do not plan to use the "Product Reviews" feature, and don't wish it to be advertised to your customers.  

1\. Look at the welcome email you received as a new customer. ( You have created an account with the shop you are developing, right?)  

2\. Find the text in that email that you wish to change.  
In this example, you desire to remove:  

```
Products Reviews - Share your opinions on products with our other customers.
```

3\. Copy a few of those words exactly to the clipboard.  
Example: `your opinions on products`

4\. Open the Developer's Toolkit under [Admin > Tools > Developer's Tool Kit](/user/admin_pages/tools/developers_tool_kit/).

5\. Paste those words "exactly" as they appeared on the email into the first search box.  

6\. From the first drop-down, choose "All Language Files"  

7\. Click *Search*

8\. You'll find that the `includes/languages/english/create_account.php` file is displayed with the exact line number where the text you desire to change is located.  

9\. Now open that file on your PC and make your changes.  

10\. Upload the changes back to your server.  

**NOTE:** It's recommended that you place your customized file in an Overrides folder, like this:  
`includes/languages/english/YOURTEMPLATE/create_account.php`

where `YOURTEMPLATE` is the name of the custom template you've been developing for your site.  

For more information on overrides see the [Template Overrides FAQ](/user/template/template_overrides/).
