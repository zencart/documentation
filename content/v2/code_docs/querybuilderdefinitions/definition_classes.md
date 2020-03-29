# definition Classes

The definitions were previously called "listing boxes", and you will 
see that this naming convention sometimes carries over.

Classes for definitions are stored in includes/library/zencart/ListingQueryAndOutput/src/definitions which should be  namespaced as ZenCart\ListingQueryAndOutput\definitions

The class definition should look like

class myDefinition extends AbstractLeadDefinition

The AbstractLeadDefinition class contains most of the logic for building definition output. The actual class that is used to build a custom definition generally needs to define only a very few methods.

Only one method must be defined 

```php
public function initQueryAndOutput()
```

There are other methods in AbstractLeadDefinition that can be overridden to allow for more customization and these will be discussed later.

# Instantiation

definitions boxes can be instantiated in 2 ways. Either as a single definition or as a group of definitions. 

## Single Box Instantiation

```php
1. $box = new ZenCart\ListingQueryAndOutput\definitions\FeaturedProductsPage($zcRequest, $db);
2. $tplVars['listingBox'] = $box->getTplVars();
```

Line 1 Instantiates the class.

Line 2 Gets the output from the class. This output is an array, and while it's format is somewhat customizable, it will always contain an array key = 'formattedItems' that will be used in the template.

Note that between line 1 and line 2 there are additional steps to build
the output of the box.

## Group Instantiation


```php
1. $listingBoxManager = new ZenCart\ListingQueryAndOutput\Manager('INDEX_DEFAULT', $db, $zcRequest);
2. $listingBoxes = $listingBoxManager->getListingBoxes ();
3. $tplVars['listingBoxes'] = $listingBoxes;
```
Line 1 instantiates the listing box group manager.

Line 2 tells the listing box manager to build all the listing boxes in the group which returns an output array.

Line 3 assigns the output to a $tplVars array.

see [Database Schema](schema)

## initQueryAndOutput()

The initQueryAndOutput method must define 2 arrays 


## listingQuery 

$this->listingQuery is an array that is used to define an SQL query. As such it has array elements to define JOIN tables, WHERE clauses, ORDER BY clauses, LIMIT clauses etc.
Other entries can define derived items, filter methods etc.

```php
        $this->listingQuery = array(
            'derivedItems' => array(
                array(
                    'field' => 'displayPrice',
                    'handler' => 'displayPriceBuilder'
                ),
                array(
                    'field' => 'productCpath',
                    'handler' => 'productCpathBuilder'
                )
            ),
            'filters' => array(
                array(
                    'name' => 'CategoryFilter',
                    'parameters' => array()
                ),
            ),
            'queryLimit' => MAX_DISPLAY_NEW_PRODUCTS,
            'joinTables' => array(
                'TABLE_PRODUCTS_DESCRIPTION' => array(
                    'table' => TABLE_PRODUCTS_DESCRIPTION,
                    'alias' => 'pd',
                    'type' => 'left',
                    'fkeyFieldLeft' => 'products_id',
                    'addColumns' => true
                )
            ),
            'whereClauses' => array(
                array(
                    'table' => TABLE_PRODUCTS,
                    'field' => 'products_status',
                    'value' => 1,
                    'type' => 'AND'
                ),
                array(
                    'table' => TABLE_PRODUCTS_DESCRIPTION,
                    'field' => 'language_id',
                    'value' => $_SESSION ['languages_id'],
                    'type' => 'AND'
                ),
                array(
                    'custom' => zen_get_new_date_range()
                )
            ),
            'orderBys' => array(
                array(
                    'field' => 'RAND()',
                    'type' => 'mysql'
                ),
            )
        );
```

## outputLayout

```php
        $this->outputLayout = array(
            'boxTitle' => sprintf(TABLE_HEADING_NEW_PRODUCTS, strftime('%B')),
            'formatter' => array('class' => 'Columnar',
                                 'template' => 'tpl_listingbox_columnar.php',
                                 'params' => array(
                                     'columnCount' => SHOW_PRODUCT_INFO_COLUMNS_NEW_PRODUCTS),
            ),
        );
```

The outputLayout array must contain the 'formatter' option. Other options are dependant on the formatter used.

More details on the fields listingQuery and outputLayout are provided in 
[Admin LEAD pages](/v2/code_docs/admin_lead_pages/introduction).
