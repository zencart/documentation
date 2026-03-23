|#|File | Version |
-|-----|---------|
|1|`includes/version.php`| alpha: `define('PROJECT_VERSION_MINOR', '2.3-alpha1');`|
|||final: `define('PROJECT_VERSION_MINOR', '2.3');`|
|2|`zc_install/includes/version.php`|alpha: `define('PROJECT_VERSION_MINOR', '2.3-alpha1');`|
|||final: `define('PROJECT_VERSION_MINOR', '2.3');`|
|||alpha and final: `define('EXPECTED_DATABASE_VERSION_MINOR', '2.0');`<br>DB version ends in zero always; doesn't change because of a patch release.|
|3|`zc_install/sql/install/mysql_zencart.sql`| Variables now specify database and project version major and minor numbers. <br>For database, do not specify patch version! CHECK CAREFULLY - look at all variables.  <br>This new system was introduced in 2.2.1; in older releases, the version information was repeated.|
|4|`zc_install/sql/updates/mysql_upgrade_zencart_220.sql`| See above.|
|5|`zc_install/includes/systemChecks.yml`|Top `checkDBVersion*` block should look for `version: '2.2.0'`|
|6|`zc_install/includes/version_upgrades.php`|`'2.2.0'=>array('required'=>'2.1.0'),`||

Shortcut for editing these 6 files: 

```
vi includes/version.php zc_install/includes/version.php zc_install/sql/install/mysql_zencart.sql zc_install/sql/updates/mysql_upgrade_zencart_220.sql zc_install/includes/systemChecks.yml zc_install/includes/version_upgrades.php
```

Note that in most cases, `includes/version.php` and `zc_install/includes/version.php` will be identical. 

