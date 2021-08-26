---
title: How to show/hide text? 
description: Using a disclosure widget
category: template
weight: 10
---

An element on a page can be toggled open or closed with just a click.

Modern web browsers support HTML5 markup language, allowing use of the `<details>` and `<summary>` elements to create a disclosure widget in which information is visible only when the widget is toggled into an 'open' state.

### Preparation:

In order for the HTML code to validate correctly when using these HTML5 elements the DOCTYPE must be set to

```
<!DOCTYPE html>
<html <?php echo HTML_PARAMS; ?>>
```

This code is in the file `includes/templates/YOURTEMPLATE/common/html_header.php`

Modern Zen Cart templates have this already but older templates may still be based on the HTML/XHTML standards. HTML5 is designed to be backwards compatible so changing the DOCTYPE on these templates should have no ill effect.

### Implementation:

The disclosure widget can be added to any page such as a [Define page](/user/template/define_pages/), [EZ-Page](/user/ezpages/), category description, product description ...

Example code

```
 <details>
  <summary>What is Zen Cart?</summary>
  <p>Zen Cart truly is the art of e-commerce; free, user-friendly, open source shopping cart software. The ecommerce web site design program is developed by a group of like-minded shop owners, programmers, designers, and consultants that think ecommerce web design could be, and should be, done differently.</p>
</details> 
```

The `<summary>` element should be the first child element of the `<details>` element.

By default the `<summary> ... </summary>` heading is all that is displayed, with the `<p> ... </p>` content being hidden. A standard arrow icon is shown next to the heading indicating that it needs to be clicked on. Try it out by copying the above code to one of your pages.

### Customization:

Although less feature rich than traditional Javascript methods of show/hide these elements can still be customized. Changing the icon, formatting the elements and changing the default state can all be achieved by edits to the HTML code or CSS stylesheet.