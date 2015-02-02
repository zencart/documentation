# Introduction

In previous versions of Zen Cart the admin home page contains a number of boxes displaying various statistics/information that may be relevant to the Shop Owner.

e.g. Recent Orders, Recent Customers. Whos-Online etc.

There are 3 problems with the current approach.

Firstly, It's not really possible for 3rd party developers to add extra boxes to that display without hacking core code.

Secondly, the information displayed is not integrated into the admin profiles system, which could potentially mean someone with a restricted admin profile seeing information that they are not authorised for.

Thirdly, there is no simple way to re-order the information so that more relevant information has higher priority.

So in v1.6 we have introduced the concept of dashboard widgets. Each widget is a self contained pairing of code/template that can be displayed on the admin home page. The store owner can drag and drop each widget, so allowing information important to the store owner to have greater priority. Widgets can be deleted from the dashboard if the store owner wishes, and they can add widgets to the dashboard even when these are provided by third parties. Widgets can be independently dynamically refreshed, so that the information they display is always relevant. Widgets can also be restricted using the Admin Profiles system used in v1.5+.

# How to build a widget

As mentioned earlier, widgets consist of 2 parts, A class file that builds the information that will be displayed in the widget, and a template that displays that information.

The class files are stored in /includes/classes/dashboardWidgets/

and the template files are stored in /includes/template/dashboardWidgets

## Class Files

```php
class zcDashboardWidgetOrderSummary extends zcDashboardWidgetBase
{
  public function prepareContent()
  {
    global $db;
    $tplVars = array();
    $orders_status = $db->Execute("select orders_status_name, orders_status_id from " . TABLE_ORDERS_STATUS . " where language_id = '" . $_SESSION['languages_id'] . "'");
 
    while (!$orders_status->EOF)
    {
      $orders_pending = $db->Execute("select count(*) as count from " . TABLE_ORDERS . " where orders_status = '" . $orders_status->fields['orders_status_id'] . "'");
 
      $tplVars['content'][] = array('text'=> '<a href="' . zen_href_link(FILENAME_ORDERS, 'selected_box=customers&status=' . $orders_status->fields['orders_status_id'], 'NONSSL') . '">' . $orders_status->fields['orders_status_name'] . '</a>', 'value'=>$orders_pending->fields['count']);
      $orders_status->MoveNext();
    }
    return $tplVars;
  }
}
```
The structure of the class file is fairly simple. The file itself should be named like class.zcDashboardWidgetWidgetName.php. The class named zcDashboardWidgetWidgetName and should extend the zcDashboardWidget class.

The actual WidgetName part will become important when we look at how we install a widget into the shop database.

The widget class needs only one function called prepareContent. (see line 3 in the example above)

This function simply prepares an array containing the information that needs to be displayed in the template, returning it as shown in line 19 above.

Also note line 6. You should ensure that the $tplVars variable is initialized as an empty array.

## Template Files

```php
<?php
/**
 * dashboard widget Template
 *
 * @copyright Copyright 2003-2013 Zen Cart Development Team
 * @license http://www.zen-cart.com/license/2_0.txt GNU Public License V2.0
 */
?>
<?php
  if (isset($tplVars['widget']['content']) && sizeof($tplVars['widget']['content']) > 0) {
    foreach ($tplVars['widget']['content'] as $entry) {
?>
      <div class="widget-row"><span><?php echo $entry['text']; ?></span><span class="right"><?php echo $entry['value']; ?></span></div>
<?php
    }
  }
```

The information returned by the Class is available in the template as the $tplVars variable.

NOTE: In a lot of cases you may not need to define your own template. Where the information you want to display consists of a 2 column report where the first column is text titles and the 2nd column is information then the tplDefault.php template should suffice.

If your template is more complex then you need to name it like 'tpl[camelized widget name].php'. So if your widget is called 'order-summary, then the template should be called 'tplOrderSummary.php'

## Installation

For third party developers creating their own widgets, installation is fairly simple:

1. Place the widget class and widget template files in the appropriate folders, as described above.
2. Insert widget definition data into the database, as described below.
3. If you have any non-super-users in your admin, use the Admin Profiles screen to assign permissions to users or profiles, so that they are available to those users to configure.

### Widget Definitions in the Database

Entries are required in these three tables:

    dashboard_widgets (TABLE_DASHBOARD_WIDGETS)
    dashboard_widgets_description (TABLE_DASHBOARD_WIDGETS_DESCRIPTION)
    dashboard_widgets_groups (TABLE_DASHBOARD_WIDGETS_GROUPS)

The dashboard_widgets table consists of 3 fields

    widget_key is a unique string representing the name/identity of the widget. This should be lower case, with words separated by hyphens. e.g. order-summary.
    widget_group is a foreign key to widget_group  in the dashboard_widgets_groups table.
    widget_status is a boolean flag which denotes whether the widget is a available for use (0 = disabled, 1 = enabled).

The dashboard_widgets_description table consists of 4 fields

    widget_key is a unique string representing the name of the widget, and must match widget_key in the dashboard_widgets table
    widget_name is the human-readable name of the widget in the specified language
    widget_description is the human-readable description in the specified language
    language_id  is the language key and must correspond to language_id entries in the languages table

The dashboard_widgets_groups table consists of 3 fields

    widget_group is the identifier name of the group - This should be lower case, with words separated by hyphens. e.g. customer-data
    language_id  is the language key and must correspond to language_id entries in the languages table
    widget_group_name is the human-readable description of the group, in the specified language

 

The Admin Profiles permissions restrictions uses the following table:

The dashboard_widgets_to_profiles table consists of 2 fields

    profile_id is an integer which corresponds to the foreign key in the admin_profiles table
    widget_key is a unique string representing the name of the widget, and must match widget_key in the dashboard_widgets table

 
When users add widgets to their own dashboard, their settings are saved in the dashboard_widgets_to_users table:

The dashboard_widgets_to_users table consists of 3 fields

    widget_key is a unique string representing the name of the widget, and must match widget_key in the dashboard_widgets table
    admin_id  is an integer value which corresponds to the foreign key in the admin table
    widget_row is the row-coordinate where the user requested the widget to appear
    widget_column is the column-coordinate where the user requested the widget to appear
    widget_refresh is the refresh cycle requested by the us
