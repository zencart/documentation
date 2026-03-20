|#|File | Version |
-|-----|---------|
|1|`includes/version.php`| alpha: `define('PROJECT_VERSION_MINOR', '2.3-alpha1');`|
|||final: `define('PROJECT_VERSION_MINOR', '2.3');`|
|2|`zc_install/includes/version.php`|alpha: `define('PROJECT_VERSION_MINOR', '2.3-alpha1');`|
|||final: `define('PROJECT_VERSION_MINOR', '2.3');`|
|||alpha and final: `define('EXPECTED_DATABASE_VERSION_MINOR', '2.0');`<br>DB version ends in zero always; doesn't change because of a patch release.|
|3|`zc_install/sql/install/mysql_zencart.sql`|`project_version_major` and `project_version_minor` for the two `Zen-Cart Main` rows should be `2` and `2.0`.<br>Do not specify patch version! Do not specify "-alpha" if pre-release!  CHECK CAREFULLY - look at all rows.|
|4|`zc_install/sql/updates/mysql_upgrade_zencart_220.sql`|`project_version_major` and `project_version_minor` should match the install file.  `project_version_comment` for the two version rows should be `Version Update 2.1.0->2.2.0`<br>Do not specify patch version! Do not specify "-alpha" if pre-release.  CHECK CAREFULLY - look at all rows.|
|5|`zc_install/includes/systemChecks.yml`|Top `checkDBVersion*` block should look for `version: '2.2.0'`|
|6|`zc_install/includes/version_upgrades.php`|`'2.2.0'=>array('required'=>'2.1.0'),`||

Shortcut for editing these 6 files: 

```
vi includes/version.php zc_install/includes/version.php zc_install/sql/install/mysql_zencart.sql zc_install/sql/updates/mysql_upgrade_zencart_220.sql zc_install/includes/systemChecks.yml zc_install/includes/version_upgrades.php
```

Note that in most cases, `includes/version.php` and `zc_install/includes/version.php` will be identical. 

