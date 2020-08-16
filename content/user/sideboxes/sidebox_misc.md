---
title: Miscellaneous Sidebox Questions 
description: Zen Cart Using Sideboxes 
category: sideboxes
weight: 2 
---

{{< misc >}} 

--- 
### How do I show my documents in their own sidebox?

You create a new category of products that describe your documents (for example, category **Recipes**), and then create products within that category (**individual recipes**). 

- In [Admin > Catalog > Categories/Products](/user/admin_pages/catalog/categories/), make your category (say it's *Recipes*).

- Edit the category, and set to product type: Document General

- Go into this category, and [create your products, the recipes](/user/admin_pages/catalog/categories_products/).

By restricting the category to Document General your Recipes category will now show in the Document Box and not the categories box.
You can add other restricted product types too, but Document General will make this one show in the Document Box and not the categories box.

---

### How do I enable/disable sideboxes on EZ-Pages? 
See the [sidebox display changes](/user/ezpages/sidebox_display_changes/) FAQ. 

---
### How do I remove and/or re-arrange the sideboxes?
See [the rearranging sideboxes](/user/template/remove_rearrange_sideboxes/) FAQ.

---
### How do I add images to a sidebox? 
See [the images in sideboxes](/user/template/add_image_box/) FAQ. 

---
### How do I remove "Page 1", "Page 2" and "Page 3" from my More Information sidebox?
Go to Admin > Configuration > Define Page Settings and set their values to 2 or 3.

---
### How do I re-arrange the order of the links in the information sidebox?

1. Create (if you don't already have it) a directory named `includes/modules/sideboxes/YOURTEMPLATE/`

2. Copy the includes/modules/sideboxes/information.php file into your new directory

3. Edit the `if` blocks into the order that you would like them to appear.

For example, if you wished the terms and conditions link to appear first, you would move this entire block of php:

```
  if (DEFINE_CONDITIONS_STATUS <= 1) {
    $information[] = '<a href="' . zen_href_link(FILENAME_CONDITIONS) . '">' . BOX_INFORMATION_CONDITIONS . '</a>';
  }
```

 (taking care not to leave the curly bracket behind) to just below the line that says:
```
  unset ($information);
```
---
### How do I change the a sidebox title?

Look in `includes/languages/YOURTEMPLATE/english.php`. 
Suppose you want the Categories sidebox to have a different title. Look for

```
define('BOX_HEADING_CATEGORIES', 'Categories');
```

Changes for other sideboxes will follow this pattern:

```
define('BOX_HEADING_XXXXXXXX', 'New Title');
```

Where `XXXXXXXX` is the name of the sidebox. 

Make the needed changes. Be sure that the single quote marks are not left out.


---
<!-- please keep this at the end --> 
{{< faq_questions >}}
