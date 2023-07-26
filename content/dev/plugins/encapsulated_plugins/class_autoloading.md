---
title: Class autoloading
description: 
weight: 35 
layout: docs
---

## Class Autoloading

Encapsulated plugins allow you to Autoload classes based on 2 scenarios.

 - Where the class follows PSR4 and the filename is the same as the class name
 - Where the filename is different to the class name

## PSR4 based classes 

Encapsulated plugins manage these automatically, by placing the classes in specific diectories.

e.g for admin I can place a class in the plugins `admin/includes/classes/` directory

As an example lets use the current DisplayLogs plugin.

In its `admin/includes/classes/` directory lets add a new class called `Cache.php`
I've named this to see how it doesn't interfere with the current cache class that Zen Cart uses.

This class looks like 

```php 
<?php

namespace Zencart\Plugins\Admin\DisplayLogs;

class Cache
{
    public function test()
    {
        echo 'FOOOOO';
    }
}
```
now in the `admin/display_logs.php` file, I can call this after the line 
```require 'includes/application_top.php';```

```php
$cache = new Cache();
$cache->test
```
Note: we also need to add 
```php
use Zencart\Plugins\Admin\DisplayLogs\Cache;
```
to the beginning of the file.

When the DisplayLogs plugin is installed we should see the `FOOOOO`output when navigating to its menu entry.

## Custom class filenames

When the filename of a class does not match the class name, we need to do a bit more work.

Again lets create a new class file in the plugin's `admin/includes/classes` directory.

Lets call this file `class.some_weird_class_filename.php`
with the contents 

```php
<?php

namespace Zencart\Plugins\Admin\DisplayLogs;

Class myClass
{
    public function test()
    {
        echo 'BARRRRR';
    }
}
```

now in the `admin/display_logs.php` file, I can add this call after the line
`require 'includes/application_top.php';

```php
$psr4Autoloader->setClassFile('Zencart\Plugins\Admin\DisplayLogs\myClass', $filePathPluginAdmin['DisplayLogs'] . 'class.some_weird_class_filename.php');
$myClass = new Zencart\Plugins\Admin\DisplayLogs\myClass();
$myClass->test();
```

This should output `'BARRRRR'` on the Display logs page in admin
