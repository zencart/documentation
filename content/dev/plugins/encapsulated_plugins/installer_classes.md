---
title: Installer Classes
description:  
weight: 30
layout: docs
---

## Installer Classes

In many cases you may not need anything custom done for a plugin beyond merely some SQL queries, which would be done in `install.sql` and removed via `uninstall.sql`. (But upgrades cannot be done merely via `.sql` files.)

However there may be times when a plugin needs to override the default installer behavior. Or handle database-changes during an Upgrade from a prior plugin version.

For example a plugin may need to check some pre-requisites before allowing installation, such as the availability of a PHP extension or maybe the plugin relies on another plugin being installed.

In these cases the plugin can define its own installer class that extends the base installer.

The class must be named `ScriptedInstaller.php` and be placed in the `Installer` directory.

e.g.

- zc_plugins

    - rewardPoints

        - v1.0.0

            - Installer

                - `ScriptedInstaller.php`

The skeleton of this class should look like :

    <?php
    use Zencart\PluginSupport\ScriptedInstaller as ScriptedInstallBase;

    class ScriptedInstaller extends ScriptedInstallBase
    { 
        /**
         * @return bool
         */
        protected function executeInstall()
        {
            return true;
        }
    
        /**
         * @return bool
         */
        protected function executeUninstall()
        {
            return true;
        }
    
        /**
         * @return bool
         */
        protected function executeUpgrade($oldVersion)
        {
            return true;
        }
    }

### Important Notes for coding in the context of a ScriptedInstaller

#### Database Querying
- Using the alternate query functions below will allow the ScriptedInstaller to report query failures so that the install aborts with a logged and displayed message.
- Avoid making `$db->` calls directly (tip: if you have to `global $db` then you're not doing it right! ... in this context.
- For non-SELECT queries, instead of `$db->Execute($sql)` use `$this->executeInstallerSql($sql)`
- For a SELECT query use `$this->executeInstallerSelectQuery($sql)` instead of `$db->Execute($sql)`
- Instead of `zen_db_perform()` use `$this->executeInstallerDbPerform()` with the same usual parameters.
- The record ID of a single record created by a db query can be accessed with `$insert_id = $this->dbConn->insert_ID();`
- The number of rows affected by a query can be accessed with `$rows = $this->dbConn->affectedRows();`
- Use `$this->dbConn->` instead of `$db->` if you really need to access the `queryFactory` object directly.
- If you need to inspect the database schema, use the `global $sniffer` class, as you normally would.

#### Database DEFINES
- NEW database TABLES need to have constants defined!!!!
    - `/catalog/includes/extra_datafiles/database_tables.php` if you need to use the table catalog-side
    - `/admin/includes/extra_datafiles/database_tables.php` if you need to use the table admin-side
    - and inside your `ScriptedInstaller.php`, at the top of the class or at least before you use the constant

#### Configuration and Configuration_Group records
- Many helper functions for `configuration` and `configuration_group` tables are shown in the example template below
- Consult `/includes/classes/PluginSupport/ScriptedInstallHelpers.php` for more insight on the many helper functions available

#### Handling Errors
- ERROR messages may be triggered via `$this->errorContainer->addError(0, 'message to log', false, 'message to show to user');`
- If errors are added to `errorContainer`, then no matter how much progress was done, the errors will be displayed in the messageStack and the plugin version will NOT be marked as installed/upgraded.
- It is best to `return false;` immediately after you trigger an error so that no further processing is done; else it will keep going and more errors will be collected.
- When returning from `executeInstall()`, `executeUninstall()`, and `executeUpgrade()`, returning `false` or triggering an error will abort and not mark it installed. If no errors are set and `true` is returned, the plugin will be marked as installed (or if upgrading, the new version will be set as the active one).

#### Building Upgrades From Prior Versions
When building upgrades in `ScriptedInstaller` remember:
- `executeInstall()` is for NEW installs, so should also include anything that an upgrade from previous version would do
- `executeUninstall()` is to remove ALL changes for the plugin even after multiple upgrades (you might choose to NOT drop columns from db, to avoid user-error by accidental uninstall of the plugin)
- `executeUpgrade()` should include ALL upgrades from ALL prior versions, since users can skip a version and therefore you need to cover all scenarios

### Example ScriptedInstaller Template

```php
<?php
use Zencart\PluginSupport\ScriptedInstaller as ScriptedInstallBase;

class ScriptedInstaller extends ScriptedInstallBase
{
    /**
     * @return bool
     */
    protected function executeInstall()
    {
        // check whether the PHP version has the required features // using mb_strtolower just as an example here
        if (!function_exists('mb_strtolower')) {

            // trigger an error, which will cause the plugin to NOT get marked as installed, AND will display the error message
            $this->errorContainer->addError(
                0,
                'error message for the log file',
                false,
                'error message for display to the user (do not include sensitive details here)'
            );
            return false; // return now to abort the rest of the installation
        }

        // probably important to de-register the page key if you're converting an old plugin and using the same key name, so the new details are correct
        if (zen_page_key_exists('myAdminPageKey')) {
            zen_deregister_admin_pages(['myAdminPageKey']);
        }
        // check if the key exists first, because re-registering will trigger errors
        if (!zen_page_key_exists('myAdminPageKey')) {
            zen_register_admin_page('myAdminPageKey', language_key, main_page, page_params, menu_key, display_on_menuYN, sort_order_int);
        }

        // read a configuration key value
        $cKey = $this->getConfigurationKeyDetails('MY_MOD_SOMETHING');

        // create a new configuration group // NOTE: YOU PROBABLY DON'T NEED A NEW GROUP, but this is an easy way to create one
        $groupId = $this->addConfigurationGroup([
            'configuration_group_title' => 'Name up to 64 characters',
            'configuration_group_description' => 'Description up to 255 chars',
            //'sort_order' => 0, // int (will be made to match auto-increment id if not specified)
            //'visible' => 1, // 0 or 1, default '1'
        ]);

        // register a configuration key
        $this->addConfigurationKey('MY_MOD_MAX_ROWS_DISPLAY', [
            'configuration_title' => 'Display Maximum Rows',
            'configuration_value' => '20',
            'configuration_description' => 'Identify the maximum number of records to display.  (Default: <b>20</b>)',
            'configuration_group_id' => 10, // could use a variable to indicate a group ID here, such as $groupId from the above example
            //'sort_order' => 100, // INT(5) default NULL
            //'use_function', // TEXT default NULL
            //'set_function', // TEXT default NULL
            //'val_function', // TEXT default NULL
        ]);

        // DATABASE CHANGES
        /** @var sniffer $sniffer */
        global $sniffer;

        define('TABLE_MY_NEW_TABLE', DB_PREFIX . 'my_new_table');
        // NOTE: Be sure to ALSO add any database table constant defines to the admin and/or catalog extra_datafiles directory.

        // Add a Table:
        if ($sniffer->table_exists(TABLE_MY_NEW_TABLE, 'some_certain_field') !== true) {
            $sql = "CREATE TABLE IF NOT EXISTS " . TABLE_MY_NEW_TABLE . " (
                id INT NOT NULL auto_increment,
                name varchar(32) default NULL,
                PRIMARY KEY (id),
                KEY idx_mynewtable_name (name)
            )";
            $this->executeInstallerSql($sql);
        }

        // Add a Field:
        if (!$sniffer->field_exists(TABLE_MY_NEW_TABLE, 'some_certain_field')) {
            $sql = "ALTER TABLE " . TABLE_MY_NEW_TABLE . " ADD some_certain_field TINYINT NOT NULL DEFAULT 0";
            $this->executeInstallerSql($sql);
        }

        // Add an index:
        if (!$sniffer->indexExists(TABLE_MY_NEW_TABLE, 'idx_certain_field')) {
            $sql = "ALTER TABLE " . TABLE_MY_NEW_TABLE . " ADD INDEX idx_certain_field (some_certain_field)";
            $this->executeInstallerSql($sql);
        }

        return true; // or false on failure
    }

    /**
     * @return bool
     */
    protected function executeUninstall()
    {
        zen_deregister_admin_pages(['yourPageKeyNameHere']);
        $this->deleteConfigurationGroup($groupName, $boolWhetherToDeleteAllConfigKeysInThisGroup);
        $this->deleteConfigurationKeys($arrayOfKeyNames);

        return true; // or false on failure
    }

    /**
     * @return bool
     */
    protected function executeUpgrade($oldVersion)
    {
        // get a configuration group ID, and optionally create it if it doesn't already exist
        $groupId = $this->getOrCreateConfigGroupId('My Group Name', 'description');

        // maybe update the title or description of the group?
        $changed = $this->updateConfigurationGroup($groupId, [
            //'configuration_group_title' => 'something', // varchar(64) NOT NULL default ''
            //'configuration_group_description' => 'something', // varchar(255) NOT NULL default ''
            //'sort_order' => 0, // int(5) default NULL
            //'visible' => 1, // int(1) default '1'
        ]);

        // maybe update parts of a configuration table record, passing only the fields that need updating for this version
        $cID = $this->updateConfigurationKey('MY_MOD_SOMETHING', [
            // 'configuration_title' => 'something',
            // 'configuration_value' => 'something',
            // 'configuration_description' => 'something',
            // 'configuration_group_id' => $groupId,
            // 'sort_order' => 'some_int', // INT(5) default NULL
            // 'use_function' => '', // TEXT default NULL
            // 'set_function' => '', // TEXT default NULL
            // 'val_function' => '', // TEXT default NULL
        ]);

        return true; // or false on failure
    }
}
```
