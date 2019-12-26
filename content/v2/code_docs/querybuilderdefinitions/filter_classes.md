# Filter Classes 

## Introduction 

Filter classes are meant to respond to URL parameters and alter the results returned from a listing box query, based on
those URL parameters.

Some examples of filters are 

### Category Filtering

Lists of products will be filtered depending on the category selected from the category sidebox.

### Alpha Filtering

Lists of products will be filtered depending on the selection from a dropdown based on the first character of the product name.
e.g. return all products that begin with `A`

### Order Filtering 

Order the list of products returned based on some arbitrary requirement.

e.g. Order by Price Low to High or Order by Model Name.

## Defining Filters

Filter actions are defined as part of the $this->listingQuery definition in the initQueryAndOutput method of a listing box class.

The filters entry will look something like :-

            'filters' => array(
                array(
                    'name' => 'DisplayOrderSorter',
                    'parameters' => array(
                        'defaultSortOrder' => PRODUCT_ALL_LIST_SORT_DEFAULT
                    )
                ),
                array(
                    'name' => 'CategoryFilter',
                    'parameters' => array(
                        'new_products_category_id' => $GLOBALS['new_products_category_id'],
                        'cPath' => $this->request->readGet('cPath', '')
                    )
                )
            ),

Each filter entry requires 2 parameters 

### name
This is the name of the class that manages the filter.
The class should be defined in the library/zencart/ListingQueryAndOutput/src/filters directory and should extend the AbstractFilter
class and implement the FilterInterface class

e.g. 
`class DisplayOrderSorter extends AbstractFilter implements FilterInterface`


### parameters

Parameters are dependant on the filter class and are passed as an array of key/value pairs.

## Filter Classes

Classes for filters are stored in includes/library/zencart/ListingQueryAndOutput/src/filters which should be namespaced as ZenCart\ListingQueryAndOutput\filters 

The class definition should look like

class CategoryFilter extends AbstractFilter implements FilterInterface

Only one method must be defined 

```php
public function filterItem(array $listingQuery);
```

which will contain the logic to carry out the filtering, and return an amended listingQuery array.

for example 

```php
class AlphaFilter extends AbstractFilter implements FilterInterface
{
    /**
     * @param array $listingQuery
     * @return array
     */
    public function filterItem(array $listingQuery)
    {
        if ((int)$this->request->readGet('alpha_filter_id', 0) == 0) {
            return $listingQuery;
        }
        $alphaSortListSearch = explode(';', '0:reset_placeholder;' . PRODUCT_LIST_ALPHA_SORTER_LIST);
        for ($j = 0, $n = sizeof($alphaSortListSearch); $j < $n; $j++) {
            if ((int)$this->request->readGet('alpha_filter_id') == $j) {
                $elements = explode(':', $alphaSortListSearch [$j]);
                $pattern = str_replace(',', '', $elements [1]);
                $listingQuery ['whereClauses'] [] = array(
                    'custom' => " AND pd.products_name REGEXP '^[" . $pattern . "]' "
                );
                break;
            }
        }
        return $listingQuery;
    }
}
```
