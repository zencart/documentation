---
title: jQuery in Zen Cart 
description: Developer information on the use of the jQuery library 
category: libraries
weight: 10
type: codepage
---

## jQuery in the Zen Cart Storefront 
The use of jQuery in the Zen Cart storefront is very much 
template dependent, with each template making its own choices.

Template Default in general will use the same version as the admin does. 

To see which jQuery version your template uses, look at `includes/templates/YOUR_TEMPLATE/common/html_header.php`.  You will see something like 

```
<script src="https://code.jquery.com/jquery-3.6.1.min.js" integrity="sha256-o88AwQnZB+VDvE9tvIXrMQaPlFFSUTR+nldQm1LuPXQ=" crossorigin="anonymous"></script>
```

which shows you version 3.6.1 is in use.

You can also open a browser window to the storefront, open the Chrome Developer Tools console and type 

```
jQuery().jquery
```

to see the jQuery version.

## jQuery in Zen Cart Admin

jQuery has been used in the Zen Cart admin since Zen Cart version 1.5.5.
The following chart shows the association between jQuery and Zen Cart versions. 

jQuery | Zen Cart Admin
-----------|--------------
jQuery 3.7.1 | ZC 2.1.0
jQuery 3.6.1 | ZC 1.5.8-2.0.1
jQuery 3.5.1 | ZC 1.5.7 
jQuery 3.4.0 | ZC 1.5.6
jQuery 1.12.4 | ZC 1.5.5

## jQuery UI

The [jQuery UI library](https://jqueryui.com/) has been used in the Zen Cart admin since 1.5.6.  

jQuery UI | Zen Cart Admin
-----------|--------------
jQuery UI 1.14.0 | ZC 2.1.x
jQuery UI 1.13.2 | ZC 1.5.8-2.0.x
jQuery UI 1.12.1 | ZC 1.5.6-1.5.7


## Help on jQuery and jQuery UI

- [jQuery](https://jquery.com/)
- [jQuery UI](https://jqueryui.com/)

