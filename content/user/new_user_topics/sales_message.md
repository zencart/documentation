---
title: How do I change the "Sales Message Goes Here" or "Tagline Here" text?
description: Removing these default text placeholders
category: new_user_topics 
weight: 10 
---

To change the `Sales Message Goes Here` or `Tagline Here` text to say what you want, do the following: 

### Instructions for 1.5.8 and above: 
Edit `includes/languages/english/YOURTEMPLATE/lang.header.php`. 
(Copy `includes/languages/english/lang.header.php` to `includes/languages/english/YOURTEMPLATE/lang.header.php` if the override file doesn't already exist.)

Find the following line of code:

```
    'HEADER_SALES_TEXT' => 'TagLine Here',
```

Replace `Tagline Here` with your own text, making sure that the single quote marks are not left out.



### Instructions for 1.5.7 and below: 

Edit `includes/languages/english/YOURTEMPLATE/header.php`.
(Copy `includes/languages/english/header.php` to 
`includes/languages/english/YOURTEMPLATE/header.php` if the override file doesn't already exist.) 

Find the following line of code:

```
define('HEADER_SALES_TEXT', 'Tagline Here');
```

Replace `Tagline Here` with your own text, making sure that the single quote marks are not left out.

