---
title: How do I change the "Congratulations! you have successfully installed..." Message?
description: Removing the installation confirmation 
category: new_user_topics 
weight: 10
---

The default `Congratulations! You have successfully installed your Zen Cart; E-Commerce Solution` text is rendered as an `H1` tag in the site template's HTML code. It is a perfect opportunity to provide some rich SEO text related to your store/business. It is best to put something useful here, instead of merely deleting it.

To edit this important text, do the following:

## Zen Cart 1.5.8 and above: 
Edit `includes/languages/english/YOURTEMPLATE/lang.index.php`.
(Copy `includes/languages/english/lang.index.php` to `includes/languages/english/YOURTEMPLATE/lang.index.php` if the override file doesn't already exist.)  

Find the following code:

```
    'HEADING_TITLE' => 'Congratulations! You have successfully installed your Zen Cart&reg; E-Commerce Solution.',
```

Replace the text starting “Congratulations” with your own text that is welcoming and describes your business. 

Make sure that the single quote marks at the beginning and end are not left out. If your text includes single-quotes (apostrophes) be sure to add a `\` before them to "escape" them for proper PHP syntax.

**NOTE: There is a similar line that starts with `'HEADING_TITLE_NESTED'`, so be sure to replace both lines.**


**NOTE:  Removing this item or setting it to `''` is a violation of Accessibility Structure requirements.**

## Zen Cart 1.5.7 and below: 
Edit `includes/languages/english/YOURTEMPLATE/index.php`. 
(Copy `includes/languages/english/index.php` to `includes/languages/english/YOURTEMPLATE/index.php` if the override file doesn't already exist.)  

Find the following code:

```
  define('HEADING_TITLE', 'Congratulations! You have successfully installed your Zen Cart&reg; E-Commerce Solution.');
```

Replace the text starting “Congratulations” with your own text that is welcoming and describes your business. 

Make sure that the single quote marks at the beginning and end are not left out. If your text includes single-quotes (apostrophes) be sure to add a `\` before them to "escape" them for proper PHP syntax.

**NOTE: This line occurs twice, so be sure to replace both lines.**

**NOTE:  Removing this item or setting it to `''` is a violation of Accessibility Structure requirements.**
