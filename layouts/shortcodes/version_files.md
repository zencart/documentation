|#|File | Version |
-|-----|---------|
|1|`includes/version.php`| alpha: `define('PROJECT_VERSION_MINOR', '2.0-alpha1');`|
|||final: `define('PROJECT_VERSION_MINOR', '2.0');`|
|2|`zc_install/includes/version.php`|alpha: `define('PROJECT_VERSION_MINOR', '2.0-alpha1');`|
|||final: `define('PROJECT_VERSION_MINOR', '2.0');`|
|3|`zc_install/sql/install/mysql_zencart.sql`|alpha: `project_version_major` and `project_version_minor` for the two `Zen-Cart Main` rows should be `2` and `2.0-alpha1`.<br>CHECK CAREFULLY - look at all rows|
|||final: `project_version_major` and `project_version_minor` for the two `Zen-Cart Main` rows should be `2` and `2.0`.<br>CHECK CAREFULLY - look at all rows|
|4|`zc_install/sql/updates/mysql_upgrade_zencart_210.sql`|alpha: `project_version_major` and `project_version_minor` should match the install file.  `project_version_comment` for the two version rows should be `Version Update 2.1.0->2.2.0-alpha1`<br><br>CHECK CAREFULLY - look at all rows|
|||final: `project_version_major` and `project_version_minor` should match the install file.  `project_version_comment` for the two version rows should be `Version Update 2.1.0->2.2.0`<br><br>CHECK CAREFULLY - look at all rows|
|5|`zc_install/includes/systemChecks.yml`|Top `checkDBVersion*` block should look for `version: '2.2.0'`|
|6|`zc_install/includes/version_upgrades.php`|`'2.2.0'=>array('required'=>'2.1.0'),`||

Shortcut for editing these 6 files: 

```
vi includes/version.php zc_install/includes/version.php zc_install/sql/install/mysql_zencart.sql zc_install/sql/updates/mysql_upgrade_zencart_220.sql zc_install/includes/systemChecks.yml zc_install/includes/version_upgrades.php
```

Note that in most cases, `includes/version.php` and `zc_install/includes/version.php` will be identical. 

