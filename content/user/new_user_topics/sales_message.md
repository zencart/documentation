---
title: How do I change the "Sales Message Goes Here" or "Tagline Here" text?
description: Removing the placeholders "Sales Message Goes Here" and "Tagline Here"
category: new_user_topics 
weight: 10 
---

To change the `Sales Message Goes Here` or `Tagline Here` text to say what you want, do the following: 

Open `includes/languages/english/header.php` in your text editor. Find the following line of code:

```
define('HEADER_SALES_TEXT', 'Tagline Here');
```

Replace `Tagline Here` with your own text, making sure that the single quote marks are not left out.

Save the edited file to `includes/languages/english/YOURTEMPLATE/header.php` and upload it to your server.

NB: By default, the text “Sales Message Goes Here” is also located in `includes/languages/english/header.php` 

```
define('HEADER_SALES_TEXT', 'Sales Message Goes Here');
```

