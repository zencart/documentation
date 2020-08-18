---
title: Relative URLs 
description: The importance of relative versus absolute links
category: first_steps 
weight: 10
---

New Zen Cart users will often customize a file like `includes/templates/responsive_classic/templates/tpl_modules_mobile_menu.php` by adding an internal URL to their store with a full path.  For example, 

```
<li>
  <a href="https://YOURSTORE.com/index.php?main_page=page&id=25">Important Pricing information</a>  <!-- NO! --> 
</li>
```

**This is not a good practice**.  This URL will not work as expected in the following circumstances: 

- You move the store to a subdomain (YOURSTORE.com/shop) 
- You change domain names 
- You work on a temporary or local domain
- You work on an IP address during a hoster change 

Instead, it is better to use a relative URL, which will always work. 

```
<li>
  <a href="index.php?main_page=page&id=25">Important Pricing information</a>
</li>
```

The same applies to the use of image tags.  In a [define page](/user/template/define_pages/), for example, it is common to reference an image starting with `/`.  

```
<img src="/images/POINTS.jpg" alt="Get Points"></p>   <!-- NO! --> 
```

The problem is, this won't work if the store is moved to a subdomain. 

If you don't start the path name with a slash, it *will* work correctly. 

```
<img src="images/POINTS.jpg" alt="Get Points"></p>
```

