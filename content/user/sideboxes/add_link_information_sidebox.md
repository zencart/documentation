---
title: Adding a Link to the Information sidebox 
description: Adding your own links 
category: sideboxes
weight: 10
---

This page continues the FAQ on [customizing the Information Sidebox](/user/sideboxes/information_sidebox/). It is such a common question is has been pulled out to its own page.

There are three techniques that can be used to add links to the "Information", [More Information](/user/sideboxes/more_information_sidebox/) and [EZ-Pages](/user/sideboxes/ezpages_sidebox/) (aka "Important Links") sideboxes. 

1. [Using a Template Override](#using-a-template-override)
2. [Using a Sidebox Module Override](#using-a-sidebox-module-override)
3. [Using an Observer](#using-an-observer).  Available for Zen Cart versions 2.0.1 and later, but [easily backported](#backporting).

## Using a Template Override

To add a link to the Information Sidebox, we create the [override file](/user/first_steps/overrides/) `includes/templates/YOURTEMPLATE/sideboxes/tpl_information.php`.  

Edit this file. 

Add your link before the list's ending `ul` tag:

```
$content  .= '</ul>' . "\n";
```

For example, linking to an external page: 

```
$content .= '<li><a href="https://www.zen-cart.com/" target="_blank" rel="noreferrer noopener">The Greatest Shopping Cart Ever!</a></li>' . "\n" ;
```

**Note:** In subsequent examples, the appended linefeed `. "\n"` is dropped for clarity. 

If the link if to an internal page, use the `zen_href_link` function.  For example, if you have a page called "News" (and have defined `FILENAME_NEWS` and `BOX_INFORMATION_NEWS`), a link to this page may be added to the Information Sidebox with 

```
$content .= '<li><a href="' . zen_href_link(FILENAME_NEWS) . '">' . BOX_INFORMATION_NEWS . '</a></li>';
```

If the link is to an internal EZ-Page, use 

```
$content .= '<li><a href="' . zen_href_link(FILENAME_EZPAGES,'id=9') . '">' . "My new page" . '</a></li>';
```

or if you don't want to modify code, you can just use the [EZ-Pages sidebox](/user/sideboxes/ezpages_sidebox/), which displays EZ-Pages with sidebox display on and a positive sort order.  

## Using a Sidebox Module Override 

Purists would argue that it's not a good practice to update the template to add links, and that instead, the relevant module file should be updated. The approach used above is more beginner friendly and lends itself to copy-and-paste ready examples for all three sideboxes, which is why it was chosen. 

You could accomplish what's done in the first example - add a link to zen-cart.com to the Information sidebox - by creating the 
[override file](/user/first_steps/overrides/) `includes/modules/sideboxes/YOURTEMPLATE/information.php`, and then modifying it just before the `require` statements to add  

```
$information[] = '<a href="https://www.zen-cart.com/" target="_blank" rel="noreferrer noopener">The Greatest Shopping Cart Ever!</a>'; 
```

The same process could be used to add a link to the More Information sidebox, using the `$more_information` array in place of `$information`. 

However, adding a link to the EZ-Pages sidebox using this technique would be more involved, since the entries in `$var_linksList` are arrays, not simple strings.

## Using an Observer

Starting with Zen Cart 2.0.1, these sideboxes include a notification to enable the insertion of additional links in the sideboxes' displays.  Each notification enables a watching observer to insert additional links into those sideboxes' display, making the template-override techniques above obsolete. 

- "Information" (`/includes/modules/sideboxes/information.php`)
- "More Information" (`/includes/modules/sideboxes/more_information.php`)
- "Important Links" (`/includes/modules/sideboxes/ezpages.php`)

Each sidebox's notification provides a numerically-indexed array of links (as HTML anchor tags) to be included in the sidebox's display.

### Information Sidebox

The "Information" sidebox now includes the following notification:

```php
$zco_notifier->notify('NOTIFY_INFORMATION_SIDEBOX_ADDITIONS', [], $information);
```

An observer can `attach` to that notification to insert additional links seamlessly into that sidebox.  Note that the Bootstrap template provides a variable (`$information_classes`) with additional classes to be included in that sidebox link.  A modification that requires support for that template as well as the built-in `responsive_classic` template should, if that variable `isset`, include that variable's value in a `class=` attribute for each inserted link. You'd have code similar to

```php
$link_class = (isset($information_classes)) ? ('class="' . $information_classes . '"') : '';
```

### More Information Sidebox

The "More Information" sidebox now includes the following notification:

```php
$zco_notifier->notify('NOTIFY_MORE_INFORMATION_SIDEBOX_ADDITIONS', [], $more_information);
```

An observer can `attach` to that notification to insert additional links seamlessly into that sidebox.  Note that the Bootstrap template provides a variable (`$more_information_classes`) with additional classes to be included in that sidebox link.  A modification that requires support for that template as well as the built-in `responsive_classic` template should, if that variable `isset`, include that variable's value in a `class=` attribute for each inserted link.  You'd have code similar to

```php
$link_class = (isset($more_information_classes)) ? ('class="' . $more_information_classes . '"') : '';
```

### Important Links Sidebox

The "Important Links" sidebox now includes the following notification:

```php
$zco_notifier->notify('NOTIFY_EZPAGES_SIDEBOX_ADDITIONS', [], $var_linksList);
```

An observer can `attach` to that notification to insert additional links seamlessly into that sidebox.

### Example Observer
 
Create the file `includes/classes/observers/auto.information_sidebox.php` as follows, using your own new links of course: 
 

```
<?php
class zcObserverInformationSidebox extends base
{
    public function __construct()
    {
        global $current_page_base;
        $this->attach(
            $this,
            [
                'NOTIFY_INFORMATION_SIDEBOX_ADDITIONS',
            ]
        );
    }

    protected function update(&$class, $eventID, $not_used, &$information)
    {

       // Your links would be appended like this: 
       $information[] = '<a class="list-group-item list-group-item-action" href="' . zen_href_link('forms') . '">' . 'Forms'. '</a>'; 

    }
}
```

### Common Observer Processing

For each of the above notifications, an observer processes the array of links provided in a similar manner.  Let's say that you want to insert the following link into one of the sideboxes:

```php
$the_link = '<a href="' . zen_href_link(FILENAME_EZPAGES, 'id=25') . '</a>';
```

If you are also supporting the Bootstrap template, you'll code that link as (based on the suggested variable name above)

```php
$the_link = '<a ' . $link_class . ' href="' . zen_href_link(FILENAME_EZPAGES, 'id=25') . '</a>';
```

Now, to insert that link into the sidebox, you can use a PHP statement similar to the following

```php
array_splice($links_array, $link_position, 0, $the_link);
```

where

- `$links_array` is the name of the variable in which you received the original array of sidebox links via the sidebox's notification.
- `$link_position` is the ***zero-based** position* at which you want to insert that link.  Use a value of `0` to insert the link as the first, `1` for the second and a large number, say `100` to insert that link at the end.
- `$the_link` is the anchor-link described above.

### Backporting 

To backport these notifiers to an earlier versions of Zen Cart, simply modify the relevant file in `includes/modules/sideboxes` (or the override folder if the file is overridden).  For example, to add the Information sidebox notifier, update `includes/modules/sideboxes/YOURTEMPLATE/information.php` and after the last link is appended to the `information` array, add: 

```
$zco_notifier->notify('NOTIFY_INFORMATION_SIDEBOX_ADDITIONS', [], $information);
```

- To backport for the EZ-Pages sidebox, modify `includes/modules/sideboxes/ezpages.php` (or the override), and add the `notify` call for `NOTIFY_EZPAGES_SIDEBOX_ADDITIONS`.
- To backport for the More Information sidebox, modify `includes/modules/sideboxes/more_information.php` (or the override), and add the `notify` call for `NOTIFY_MORE_INFORMATION_SIDEBOX_ADDITIONS`.

## General Information

### Specification of URLs 

It's a good practice not to hardcode non-relative URLs, in case your site moves or you want to reconstruct a test instance of it.  So don't do this: 

```
$content .= '<li><a href="https://YOURSTORE.com/index.php?main_page=page&id=25">Important information</a></li>'; // NO 
```

Instead, use an URL relative to the top of your store (or better yet, use `zen_href_link` as in the examples above): 
```
$content .= '<li><a href="index.php?main_page=page&id=25">Important information</a></li>'; // Better
```

You can read more about [the importance of relative URLs](/user/first_steps/relative_urls/) to explore this topic in greater depth. 


### Mobile

You may need to make [additional edits to control the link on mobile displays](/user/template/sideboxes/#controlling-sideboxes-on-mobile-menu).

### More Examples 
See [creating links to other pages](/user/customizing/creating_links/). 
