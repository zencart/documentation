---
title: A DTO to define Tabular data
description: A data transfer object that defines the columns used in tabular data
weight: 100 
layout: docs
---

**fixme: This page is still under construction, and will change during the 
v158 branch changes.**

When displaying tablular data we need to define the columns we want to
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
 - actions: fixme blah blah
 
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
 to be an instance of `illuminate\Pagination\LengthAwarePaginator` then 
 if paginated is set to false we do still paginate the results, but with a 
 `maxRowCount` of 100000.
 
## pagerVariable
 
 **default: page**
 
 The name of the GET parameter that holds the current page number
 
## actions
 
 @todo
 
## columns
  
A description of the columns that are to be displayed.

The query result for a table will generally return all the fields for
that table, however we may not want to show all those fields, and further
may want to add columns that display data that is derived from the database
table. 
  

 
 
