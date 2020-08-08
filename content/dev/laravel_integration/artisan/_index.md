---
title: Laravel Artisan
description: A command line interface
weight: 100 
layout: docs

---

Laravel Artisan is a command line application that allows for running 
commands that help with the management of a Laravel application.

See the [Laravel documentation](https://laravel.com/docs/7.x/artisan) for further details.

Most of the in-built commands currently have little relevance for use 
in a Zen Cart application, although that may change over time.

You can run the artisan command by changing into the `laravel` directory 
and running the `./artisan` command

This will list all of the commands available.

For Zen Cart, we have added the following command(s).

`make:defines`

## `make:defines` command


The make:defines command is used to convert legacy language files into the new php array format.

The command accepts the following options 

    --file 
    --dir
    --config
    --force 
    
At least one of `--file`, `--dir`, `--config` must be set. 
The `--force` command is optional.

### --file

This option accepts the path to a single file. 

e.g `admin/includes/languages/english/index.php`

and will convert that file to 

`admin/includes/languages/english/lang.index.php`

### --dir

This option accepts the path to a directory.

It will attempt to convert all files within the directory renaming files with a `lang.` prefix.

### --config

This option accepts the path to a file containing an array definition used to decide which files to convert.

The config file is an array return file, so should look like 

    <?php 
    return [];
    
    
The array can have 2 root elements, `files` and `directories`

`files` is a list of files to convert, and similarly `directories` is a list of directories to convert.

e.g. 

    <?php 
    return [
        'files' => ['file1.php', 'file2.php],
        'directories' => ['dir1', 'dir2']
    ];


### --force

The parser used to convert files will produce incorrect output in various scenarios.
e.g. This define 

```
define('TEXT_TEST', 'All Language Files for ' . strtoupper($_SESSION['language']) . ' - Catalog/Admin');
```

will not be parsed correctly, and in general any define that contains php functions etc. will not be.

The `make:defines` command will report that the file to be converted contains tokens that can not be converted,
and conversion of that file will be suppressed.

The `--force` command will override the suppression, and the new `lang.` file will be created, albeit in a form that 
will probably generate errors.
The generated file in question should then be manually edited to fix any problems.
