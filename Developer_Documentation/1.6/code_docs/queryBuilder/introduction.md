# Introduction

The Querybuilder class allows for the construction of sql queries based on an array format to define base tables, foreign keys, select options, where options and other options. 
It is used by a number of other classes, such as listingBoxes, LEAD pages etc.

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

## mainTableName
## mainTableAlias
##mainTableFkeyField
## tableAliases
## selectList
## filters
## derivedItems
## joinTables
## whereClauses
## orderBys
