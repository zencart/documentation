---
title: Tools in Habitat
weight: 5
---

Development Tools
=================

More coming Soon


phpMyAdmin
----------

phpMyAdmin is pre-installed on the vm, and can be easily accessed via `http://172.22.22.22/phpmyadmin` and logging in as zencart/zencart.

###TIP:
>For easy importing of .sql files, note that on your host PC there is a `habitat/tmp` folder. This is shared with phpMyAdmin and makes quick importing of .sql files very simple.

>1. Simply copy any desired .sql files to your host PC's `habitat/tmp` folder
2. Open phpmyadmin in your browser, `select a database`, and then click the `Import` button. There will be a dropdown available with a list of all the .sql files above.


Database Backup and Restore
---------------------------

**BACKUP**

To do a complete backup of all databases in the vm:

1. ssh into the habitat vm, so you have a command-line prompt
2. cd into the folder that you've shared back to your host machine
3. Enter this command to tell MySQL to dump all databases to a single gzipped file using the current date/time stamp as the filename:

>
`Command Line`
>
mysqldump -u zencart -pzencart  --all-databases  --hex-blob | gzip -9 > ./habitat_$(date +%Y-%0m-%0d_at_%0I_%0M_%0p.sql.gz)


**RESTORE**

Similarly, to restore:

1. Put the "backup" file into your shared folder
2. Unzip it so the file is a .sql file with text content (not zipped)
3. ssh into the habitat vm
4. cd into the shared folder
5. Use the following command to initiate the restore, replacing HABITAT_FILENAME with the actual filename of your .sql file (ie: `habitat_YYYY-MM-DD_at_HH_MM.sql`):

>
`Command Line`
>
mysql -u zencart -pzencart < HABITAT_FILENAME



Unit Testing
------------

Habitat includes a helper script to help with running unit tests within the Zen Cart testFramework.  This depends on having `localize_tools:` and `do_default\_map:` set to true in your yaml file. It may encounter some difficulties if the `folders:map` or `folders:to` settings have been customized.

From the command line you can do
>
`Command Line`
>
cd habitat/tools  
./unittest DIRNAME

The option given to the unittest script is a reference to a site in your habitat VM. In other words it should match the `dir` option given in a `sites:` block of your yaml file. To run the tests on the `develop` branch, on your host machine you'd use `./unittest develop`


phpDocumentor
-------------

Habitat also includes a helper script to generate phpDocumentor output, which will be placed in the `DIRNAME/docs/phpdocs` folder.

Syntax is similar to the unit-testing above, and depends on the same prerequisites.

>
`Command Line`
>
cd habitat/tools
./generatedocs DIRNAME

