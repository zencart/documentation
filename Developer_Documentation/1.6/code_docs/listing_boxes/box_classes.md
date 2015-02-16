# Box Classes

Classes for listing boxes are stored in includes/library/zencart/listingBox/src/Box which should be  namespaced as ZenCart\ListingBox\Box 

The class definition should look like

class AllDefault extends AbstractListingBox

The AbstractListingBox class contains most of the logic for building listing box output. The actual listing box class that is used to build a custom listing box generally needs to define only a very few methods.

Two methods that must be defined are

```php
public function __construct()
```
and

```php
public function initTitle()
```

There are other methods in AbstractListingBox that can be overridden to allow for more customization and these will be discussed later.

# Instantiation

Listing boxes can be instantiated in 2 ways. Either as a single listing box or as a group of listing boxes.

## Single Box Instantiation

```php
1. $box = new \ZenCart\ListingBox\Build ($zcDiContainer, new \ZenCart\ListingBox\Box\ProductsDefault());
2. $box->init();
3. $tplVars['listingBox'] = $box->getTemplateVariables ();
```

Line 1 Instantiates the class.

Line 2 Runs the init method of the Listing Box Class.

Line 3 Gets the output from the Listing box class. This output is an array, and while it's format is somewhat customizable, it will always contain an array key = 'formattedItems' that will be used in the template.

In Line 1 when instantiating the class we use the Listing Box build class. This takes 2 parameters.

The first parameter is a Dependency Injection container that is now created by default by the Zen Cart InitSystem and stored in a global variable $zcDiContainer.
The second parameter is an instantiation of the Listing Box class we want to build, in the example above, this is the ProductsDefault class.

## Group Instantiation


```php
1. $listingBoxManager = new \ZenCart\ListingBox\Manager();
2. $listingBoxes = $listingBoxManager->buildListingBoxes ('INDEX_DEFAULT', $zcDiContainer);
3. $tplVars['listingBoxes'] = $listingBoxes;
```
Line 1 instantiates the listing box group manager.

Line 2 tells the listing box manager to build all the listing boxes in the group which returns an output array.

Line 3 assigns the output to a $tplVars array.

see [Database Schema](schema.md)

## _construct method

The _construct method must define 2 arrays, using 


__$this->setProductQuery()__

and

__$this->setOutputLayout()__

## productQuery 

$this->productQuery is an array that is used to define an SQL query. As such it has array elements to define JOIN tables, WHERE clauses, ORDER BY clauses, LIMIT clauses etc.

```php
        $this->setProductQuery(array(
            'isRandom' => false,
            'isPaginated' => true,
            'filters' => array(
                array(
                    'name' => 'DisplayOrderSorter',
                    'parameters' => array(
                        'defaultSortOrder' => PRODUCT_ALL_LIST_SORT_DEFAULT
                    )
                )
            ),
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
            'joinTables' => array(
                'TABLE_PRODUCTS_DESCRIPTION' => array(
                    'table' => TABLE_PRODUCTS_DESCRIPTION,
                    'alias' => 'pd',
                    'type' => 'left',
                    'fkeyFieldLeft' => 'products_id',
                    'addColumns' => true
                ),
                'TABLE_MANUFACTURERS' => array(
                    'table' => TABLE_MANUFACTURERS,
                    'alias' => 'm',
                    'type' => 'left',
                    'fkeyFieldLeft' => 'manufacturers_id',
                    'addColumns' => true
                )
            ),
            'whereClauses' => array(
                array(
                    'table' => TABLE_PRODUCTS_DESCRIPTION,
                    'field' => 'language_id',
                    'value' => $_SESSION ['languages_id'],
                    'type' => 'AND'
                ),
                array(
                    'table' => TABLE_PRODUCTS,
                    'field' => 'products_status',
                    'value' => 1,
                    'type' => 'AND'
                )
            )
        ));
```

## outputLayout

The outputLayout array must contain the 'formatter' option. Other options are dependant on the formatter used.

See Listing Box Formatter Classes for more details.

