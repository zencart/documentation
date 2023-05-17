---
title: How do I change the "Sales Message Goes Here" or "Tagline Here" text?
description: Removing these default text placeholders
category: new_user_topics 
weight: 10 
---

To change the `Sales Message Goes Here` or `Tagline Here` text to say what you want, do the following: 

### Instructions for 1.5.8 and above: 
Open `includes/languages/english/YOURTEMPLATE/lang.header.php` in your text editor. (Create it from `includes/languages/english/lang.header.php` if it doesn't exist.) Find the following line of code:

```
    'HEADER_SALES_TEXT' => 'TagLine Here',
```

Replace `Tagline Here` with your own text, making sure that the single quote marks are not left out.

Save the edited file and upload it to your server.



### Instructions for 1.5.7 and below: 

Open `includes/languages/english/YOURTEMPLATE/header.php` in your text editor. (Create it from `includes/languages/english/header.php` if it doesn't exist.)  Find the following line of code:

```
define('HEADER_SALES_TEXT', 'Tagline Here');
```

Replace `Tagline Here` with your own text, making sure that the single quote marks are not left out.

Save the edited file and upload it to your server.

