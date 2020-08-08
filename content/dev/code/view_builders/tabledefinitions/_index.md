---
title: A DTO to define Tabular data
description: A data transfer object that defines the columns used in tabular data
weight: 100 
layout: docs
---

**fixme: This page is still under construction, and will change during the 
v158 branch changes.**

When displaying tabular data we need to define the columns we want to
display along with some metadata as to how the table will appear.

The table definition DTO holds that data in an object that can be passed
to other classes that manipulate it, to provide a final output.

The basic definition consists of a number of entries.

 - colKeyName: the get parameter name that passes the primary key
 - colKey: The primary key of the table being displayed
 - maxRowCount: The number of entries to be displayed using pagination
 - columns: A definition of the columns to be displayed for the table
 - paginated: whether the results are paginated or not
 - pagerVariable: the name of the get parameter that holds the current page
 - buttonActions: buttons to do certain action, e.g. new entry et.
 - rowActions: actions that affect just a row in the table
 
## colKeyName
 
 **default: colKey**
 
 In legacy Zen Cart admin, table views might have used something like
 pID, or cID etc. In general there is no reason to change from the default
 unless it is to support legacy plugins.
 
## colKey
 
 **default: id**
 
 The name of the unique primary key for the database table being displayed 
 
## maxRowCount
 
 **default: 10**
 
 The maximum number of rows to be displayed per paginated page.
  
## paginated
 
 **default: true**
 
 Whether the table data should be paginated or not.
 
 **Note:** as an implementation detail, and because we force final query results
 to be an instance of `illuminate\Pagination\LengthAwarePaginator`, then 
 if paginated is set to false, we do still paginate the results, but with a 
 `maxRowCount` of 100000.
 
## pagerVariable
 
 **default: page**
 
 The name of the GET parameter that holds the current page number
 
## buttonActions
 
 Button actions are for displaying buttons that carry out some global action.
 e.g. creating a new entry for a table.
 
 The array format for an entry in the `buttonActions` array is 
 
  - action: the name of the action to be carried out
  - whitelist: a list of actions that allow the button to be displayed
  - blacklist: a list of actions that prevent the button being displayed
  - linkParams: info on how to build extra parameters for the button link
  - title: The text to be displayed as the button title
  - buttonClass: a bootstrap class applied to the button
  
  The `linkParams` entry contains
  
  - source: for now only `request` is allowed
  - field: the name of the request param to use
  - param: the name of the GET param added to the link
  
example:   

## rowActions
  
  row actions are buttons that appear along side every row in a table, 
  and use the data in that row to carry out some action.
    
  The array format for an entry in the `rowActions` array is 
  
  - action: the name of the action to be carried out. 
  - icon: the name of a [Fontawesome](/user/template/font_awesome/) icon to display
  - linkParams: info on how to build extra parameters for the 
                buttons link.
                
  The linkParams entry contains 
  
  - source: for now only `tableRow` is allowed.
  - field: the field from the source to be used
  - param: the name of the GET param added to the link
  
example:

    'linkParams' => [
        [
        'source => 'tableRow',
        'field' => 'status',
        'param => 'status'
        ]
    ]
    
for the above a link would be built with the following added

    'status={value of tableRow status}
    
by default the link built for the row would point to the current page and 
include the paginator page variable, so again for the above the full link
would be for admin

    cmd=somepage&page=1&status=0;
    
## columns
  
A description of the columns that are to be displayed.

The query result for a table will generally return all the fields for
that table, however we may not want to show all those fields, and further
may want to add columns that display data that is derived from the database
table. 

The definition consists of an entry for each column we want to display in the table.

e.g. 

```
   'columns' = [
        'name' => []
    ]
```
  
The `key`,in this case `name` refers to the field in the database for the 
table (unless this is a derived item)

For an entry that refers to a database field, there would be 2 possible entries.

e.g. 

```
   'columns' = [
        'name' => [
             'title' => ,
              'class' => 
        ]
    ]
```

# Class Methods

There are various class methods to allow for manipulation of the TableView definition

## public function getDefinition()

## public function setParameter(string $name, $value)

## public function addParameter(string $field, $definition)

## public function getParameter(string $field)

## public function addButtonAction($definition)

## public function addRowAction($definition)

## public function addColumn(string $field, $definition)

## public function addColumnBefore($index, $newKey, $data)

## public function addColumnAfter($index, $newKey, $data)

## public function getHeaders()

## public function isPaginated()

## public function colKeyName()

## public function hasRowActions()

## public function getRowActions()

## public function getButtonActions()


