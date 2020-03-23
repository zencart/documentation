---
title: Template Overrides System 
description: Zen Cart Template Overrides System 
category: template 
weight: 10
---

## Introduction

The template system exists mainly for 2 reasons:

*   To allow you to design multiple appearances of your store for perhaps seasonal themes, etc.
*   To make upgrading easy

The template system consists of at least 3 parts:

*   Database settings
*   The override system
*   Automatically included files

See [how to create a new template](/user/template/creating_template).

See [how to customize your new template](/user/template/customizing_template).

## Database settings

These can all be configured from the Administration area. 

## Override system

The template system may some times be refered to as the 'override' system in the context of editing files.

Also see: [Developers' overrides ](/user/template/developers_overrides/). 

<dl>

<dt>Override system </dt>

<dd>When Zen Cart™ is about to read a template file, it will first see if there exists an override of that file, but if there's no such override, it will include the default/core file.</dd>

</dl>

**Whenever you plan to make changes to a file, see if it can be overridden first.**  
Files can be overridden if

*   The directory where the file resides holds a sub-directory named "classic".
*   The current path includes "template_default" or a template directory, such as "classic". Eg. /includes/templates/template_default/common/

Unfortunately, not all files can be overridden at this time. Nothing under the admin directory can be overridden yet.

**If the file you plan to edit can be overridden, follow these steps:**

1.  Create a new directory so the new path is equal to the old one except it includes your template directory, and no other template directory, in the proper location.  
    **Examples to demonstrate the basic patterns. Other override directories follow these patterns.**  
    _The directory where the file resides holds a sub-directory named "classic"._

```
    Default path: includes/languages/
    Override path: includes/languages/YOURTEMPLATE/

    Default path: includes/languages/english/ 
    Override path: includes/languages/english/YOURTEMPLATE

```

The current path includes "template_default" or a template directory, such as "classic" or "blue_stripe".

```
Default path: includes/templates/template_default/common/
Override path: includes/templates/YOURTEMPLATE/common/

Default path: includes/templates/template_default/templates/
Override path: includes/templates/YOURTEMPLATE/templates/

Default path: includes/templates/template_default/buttons/english/
Override path: includes/templates/YOURTEMPLATE/buttons/english/
```

1.  Copy the file you plan to edit, and **only** the file you plan to edit, into the new directory.
2.  Edit the newly copied file.

Remember that the default core files will be used for all the files that are **not** being overridden, so you don't need to override files that you haven't made changes to.

If you remember to always use the template/override system when editing files, you should have no major problems when upgrading.  
If you don't do that, all your files will be overwritten when you upgrade.

Other things you need to be aware of:

*   The directory 'includes/templates/template_default' contains many of the default/core template files, but "template_default" is not a normal template - it's only the location of those default template files.
*   Remember that the Classic template will be overwritten whenever you upgrade to a new version. In other words; don't use the Classic template. You should create your own template and avoid this problem instead.
*   The Classic template is the default template, but it exists only to be an example for your own custom template.
*   Text is placed inside language files, located beneath the directory 'includes/languages'. If you're looking to replace some text, this is the place to look.

## Automatically included files

Files residing inside the following directories will automatically be included.

- `includes/extra_configures`

- `includes/extra_datafiles`

- `includes/functions/extra_functions`

- `includes/languages/YOUR_LANGUAGE/extra_definitions` or the appropriate override directory if the file exists there.

- `includes/templates/YOURTEMPLATE/jscript/` - see the file `read_me_jscript.html` in that directory for instructions.

- `includes/templates/YOURTEMPLATE/jscript/on_load/` - see the file `read_me_onload.html` in that directory for instructions.

- `includes/templates/YOURTEMPLATE/css/` - all filenames that start with "style".

- `includes/modules/pages/CURRENTPAGE/` - all filenames that start with `"jscript_"` and ends with ".php".

See any already existing files in those directories for clues about what kind of data they're meant for.

## Getting Started

First, you want to make sure you're using your own template, as opposed to the default templates which will get overwritten by an upgrade, so go ahead and create a new template.  

See [how to create a new template](/user/template/creating_template).

See [how to customize your new template](/user/template/customizing_template).

Now that you know how to use the template system and have created and activated your own template, how would you go ahead in order to find the correct file for the changes you want to do?  

Learn to use the [Developers Tool Kit](/user/admin/developers_toolkit) available from the administration area.  It will help you track down the files that you need to change. 

See also [this related FAQ](/user/template/what_files). 


