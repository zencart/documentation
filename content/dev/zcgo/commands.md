---
title: Commands
weight: 20
---

## make:defines

The make:defines command is used to convert legacy language files into the new php array format.

The command accepts up to 3 options 

    -f --file 
    -d --dir
    -c --config
    
    
### -f --file

This option accepts the path to  single file. 

e.g `admin/includes/languages/english/index.php`

and will convert that file to 

`admin/includes/languages/english/lang.index.php`

`
### -d --dir

This option accepts the path to a directory.

It will attempt to convert al files within the directory renaming files with a `lang.`
prefix.

### -c --config

This option accepts the path to a file that contains an array definition used to decide 
which files to convert.

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

## make:idehelper
