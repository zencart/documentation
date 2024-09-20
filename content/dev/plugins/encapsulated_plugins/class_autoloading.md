---
title: Class autoloading
description: 
weight: 35 
layout: docs
---

## Class Autoloading
"Class Autoloading" means: "when I want to use a class, I simply attempt to instantiate it (ie: `new Foo()`) and PHP will automatically find the right file, load it (so I don't have to `include()` or `require()` it manually), and then do the requested creation of an instance of it". In most cases this is the best way.

Encapsulated plugins allow you to Autoload classes based on 2 scenarios.

 - Where the class follows PSR4 and the filename is the same as the class name (This is the best way). Naming should be CamelCased.
 - Where the filename is different to the class name (This should be rare).

## PSR4 based classes 

Formula for catalog:
- place your class in the plugin's `[version]/catalog/includes/classes/` directory
- name the class and its filename the same (ie: `includes/classes/DrawPrettyGraph.php` should contain a class named `DrawPrettyGraph`)
- set the `namespace`: `namespace Zencart\Plugins\Catalog\SalesGraphs;` if the plugin's name is `Sales Graphs`

Formula for admin:
- place your class in the plugin's `[version]/admin/includes/classes/` directory
- name the class and its filename the same (ie: `admin/includes/classes/DrawPrettyGraph.php` should contain a class named `DrawPrettyGraph`)
- set the `namespace`: `namespace Zencart\Plugins\Admin\SalesGraphs;` if the plugin's name is `Sales Graphs`

Example, for a plugin named `Sales Graphs`:
Filename: `zc_plugins/SalesGraphs/vX.Y/admin/includes/classes/DrawPrettyGraph.php` containing:
```php 
<?php
namespace Zencart\Plugins\Admin\DisplayLogs;

class DrawPrettyGraph
{
    public function output()
    {
        echo 'Look at my pretty graph!';
    }
}
```
now in any file you can invoke it directly:
`$myGraph = (new ZenCart\Plugins\Admin\SalesGraphs\DrawPrettyGraph)->output();`

Or if you'd like to split the namespace out separately, use 2 steps:
- At the top of whatever file you wish to use it, add a line: `use Zencart\Plugins\Admin\SalesGraphs\DrawPrettyGraph;`
- Then call it: `$myGraph = (new DrawPrettyGraph)->output();`


## Custom class filenames

When the filename of a class does not match the class name, we need to do a bit more work.

From the example above, if we had a class filename of `class.some_weird_class_filename.php` and the class name was `myClass`, then we would have to set up autoloading manually at tthe top of whatever file needs it. The following would need to be called after the line
`require 'includes/application_top.php';`:

```php
$psr4Autoloader->setClassFile('Zencart\Plugins\Admin\SalesGraphs\myClass', $filePathPluginAdmin['SalesGraphs'] . 'class.some_weird_class_filename.php');
$myClass = new Zencart\Plugins\Admin\SalesGraphs\myClass();
$myClass->output();
```

This would output `'Look at my pretty graph!'`
