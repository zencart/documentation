---
title: How do I change the "Congratulations! you have successfully installed..." Message?
description: Removing the installation confirmation 
category: new_user_topics 
weight: 10
---

The default `Congratulations! You have successfully installed your Zen Cart; E-Commerce Solution` text is rendered as an `H1` tag in the site template's HTML code. It is a perfect opportunity to provide some rich SEO text related to your store/business. It is best to put something useful here, instead of merely deleting it.

To edit this important text, do the following:

Open the `includes/languages/english/index.php` file and find the following code:

```
  define('HEADING_TITLE', 'Congratulations! You have successfully installed your Zen Cart&reg; E-Commerce Solution.');
```

Replace the text starting “Congratulations” with your own text that is welcoming and describes your business. 

Make sure that the single quote marks at the beginning and end are not left out. If your text includes single-quotes (apostrophes) be sure to add a `\` before them to "escape" them for proper PHP syntax.

**NOTE: This line occurs twice, so be sure to replace both lines.**

Save the edited file to `includes/languages/english/YOURTEMPLATE/index.php` and upload it to your server.

