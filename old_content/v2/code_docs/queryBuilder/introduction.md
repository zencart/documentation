# Introduction

The QueryBuilder class allows for the construction of sql queries based on an array format to define base tables, foreign keys, select options, where options and other options. 
It is used by a number of other classes, such as ListingQueryAndOutput, LEAD pages etc.

While initially written to produce queries against the Products Table, it can be used to produce queries against any table used by Zen Cart.

# Instantiation

Instantiation of the class would look like 

$qb = new ZenCart\QueryBuilder\QueryBuilder($db, $queryBuilderDefinition);

where $db is a instance of QueryFactory and 
$queryBuilderDefinition is an array defining the query to be executed.

Sometimes the $queryBuilderDefinition would be empty or not defined at the point of instantiation, as we may want to inject a clean object and later use the process method to pass the actual array.

so we can instantiate and run the query builder in two ways.

# queryBuilderDefinition

Whether we pass the definition in the constructor or the process method, the definition can include the following entries.

+ mainTable
+ mainTableName
+ mainTableAlias
+ mainTableFkeyField
+ tableAliases
+ selectList
+ filters
+ derivedItems
+ joinTables
+ whereClauses
+ orderBys


## mainTable

If set the mainTable entry should consist of an array.

e,g, 

['mainTable'] = array('table' => TABLE_PRODUCTS, 'alias' => 'p', 'fKeyFieldLeft' => 'products_id');

The 'table' entry wil be mapped to 'mainTableName'
The 'alias' entry will be mapped to 'mainTableAilas'
The 'fKeyFieldLeft will be mapped to the 'mainTableFKeyField'

## mainTableName

Optional, and by default is set to TABLE_PRODUCTS.
Or set by ['maintable']['name']

## mainTableAlias

Optional and by default is set to 'p'
Or set by ['maintable']['mainTableAlias']

## mainTableFkeyField

Optional and by default is set to 'products_id'
Or set by ['maintable']['fkeyFieldLeft']

## tableAliases

Associates a table alias with a table name. 
Generally these associations are handled internally for the main table and join tables.  
However if needed take the form of 

## selectList

Generally the fields selected from a query are managed automatically. However there are times when you may want to add something to the select list, especially if you want to alias it.


## filters

## derivedItems

## joinTables

## whereClauses

## orderBys

# Examples

