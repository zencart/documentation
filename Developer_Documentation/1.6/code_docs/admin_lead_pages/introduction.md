Introduction
============

The Zen Cart Administration Interface contains a number of pages that are used to manage simple lists of items. Examples are the Countries and Zones pages under Locations/Taxes.

What is common amongst these pages is that they initially show a paginated list of entries, and then allow you to edit an existing entry, add new entries, and delete entries.

The current pages that manage these lists have a number of problems. They are difficult to create easily, they are almost impossible to customize using add-ons and the code is usually quite messy, with php code interspersed with output HTML.

The new style admin LEAD (List/Edit/Add/Delete) pages are completely object oriented. Code is separate from the output templates. They are easy to create, in fact a lot of LEAD pages can be created by simply defining some simple array structures.

The LEAD pages also integrate a simple filtering system, that allows the admin user to select a subset of the items in the list.

LEAD pages leverage a number of new classes/structures which have been added to v160:

* Admin Action Controllers define a new way of writing admin pages, where the code is separated from the template.
 
* Listing Box classes allow for complex querying of the database using a structured array.
  
* Service classes that separate domain specific concerns from the controllers.

We will show examples of using all three of the above classes in the documentation.

LEAD Controllers
================

New pages that are being written for Zen Cart admin should use the new controller classes. Documentation for controller classes can be found here.

Generally the controller classes for Admin LEAD pages are very simple. 

e.g. 

```
<?php
namespace ZenCart\Controllers;

/**
 * Class Countries
 * @package ZenCart\Controllers
 */
class Countries extends AbstractLeadController
{
}
```

There may be reasons to override methods in the AbstractLeadController and examples will be given later.

LEAD Controller names are expected to follow Camel Case conventions.  So 
for the command `admin/index.php?cmd=geo_zones`, the Controller would be `GeoZones.php` in `includes/library/zencart/Controllers/src/admin/`.

QueryBuilderDefinitions Classes
==============================

The main workhorse of the LEAD pages are the QueryBuilderDefinitions classes.

QueryBuilderDefinitions file names are also expected to follow Camel Case conventions, and to start with the string "Lead".  So 
continuing with the example `admin/index.php?cmd=geo_zones`, the QueryBuilderDefinitions 
would be `LeadGeoZones.php` in `includes/library/zencart/QueryBuilderDefinitions/src/definitions/`.

Reports (pages using the LEAD infrastructure but without edit, add or delete
capability) start with "ReportStats" instead of "Lead".  So for the report 
which is reached using `admin/index.php?cmd=stats_products_lowstock`, 
the corresponding QueryBuilderDefinitions class  
would be `ReportStatsProductsLowStock.php` in `includes/library/zencart/QueryBuilderDefinitions/src/definitions/`.

The QueryBuilderDefinitions object is built out in the call initQueryAndLayout().

### Objects in QueryBuilderDefinition:
* listingQuery - array of fields controlling the query of data to be displayed
* outputLayout - array of fields controlling how the data will be displayed 


#### Fields in listingQuery
* mainTable - The first table in the query (array)
* joinTables - Additional tables in the query which are joined with a foreign key (array) 
* whereClauses - The WHERE statement used in the query (array)
* language - Flag which indicates the table has translations (boolean, default false)
* singleTable - Flag which indicates whether translations are in the same table vs another table (boolean, default: false)
* languageInfoTable - Table where translations are stored (string)
* languageKeyField - some tables use `languages_id` and some use `language_id` as their key; this field indicates which value to use (string, default: `languages_id`) 
* isPaginated - Whether all results should be shown on one page, or broken up so that only a specific number are displayed with navigation buttons to go forward and backward in the complete set (boolean, default true)
* pagination - Structure controlling display of pagination controls (array)

  
#### Fields in outputLayout 
* relatedLinks - Second set of boxes on the left hand side of a LEAD page (array of arrays)
* listMap - The order in which the fields are displayed when viewing the list (array of strings)
* editMap - The order in which the fields are displayed when editing an entry (array of strings)
* showActionLinkListList - The first set of boxes on the left hand side of a LEAD Page (boolean, default true) 
* allowAdd - Whether or not you are allowed to add new items to this list (boolean, default true). 
* fields 
* fieldFormatter
* formatter 

##### Fields in outputLayout->fields 

example:
```
                'artists_url' => array(
                    'bindVarsType' => 'string',
                    'language' => true,
                    'layout' => array(
                        'common' => array(
                            'title' => TEXT_ENTRY_RECORD_ARTIST_URL,
                            'type' => 'text',
                            'size' => '30'
                        )
                    )                    
```


Language Handling
=================

## Language Files 

Language file names have the name of the command, so using again the example of the low stock report `admin/index.php?cmd=stats_products_lowstock`, 
the language file would be 
`includes/languages/english/stats_products_lowstock.php`.  

The only rules around strings in this file relate to the strings required by the LEAD framework.  The "List" button, which is the first of the buttons on the left side of the LEAD page, requires the define `TEXT_LEAD_ACTION_LIST`.
The "Add" button requires the define `TEXT_LEAD_ACTION_ADD_ENTRY`.  


## Language Handling in Queries

Some queries which join tables containing a language key field will need to use only the current language.  This is specified in the `whereClauses` and `bindVars` of the `listingQuery`.  

```
            'whereClauses' => array(
                array(
                    'type' => 'AND',
                    'table' => TABLE_PRODUCTS_DESCRIPTION,
                    'field' => 'language_id',
                    'value' => ':language_id:'
                )
            ),  
            'bindVars' => array(
                array(
                    ':language_id:',
                    $_SESSION ['languages_id'],
                    'integer'
                )   
            ),  
```
 
For an example of this, see `includes/library/zencart/QueryBuilderDefinitions/src/definitions/LeadGeoZonesDetail.php
