# Formatter Classes

Formatter classes take the ordered list of items that are produced by the listingBox/queryBuilder and format them into an array that an output template can use.

## Defining Formatters

Formatter are defined as part of the $this->outputLayout definition in the initQueryAndLayout method of a listing box class.

e.g. 

```php
        $this->outputLayout = array(
            'boxTitle' => sprintf(TABLE_HEADING_NEW_PRODUCTS, strftime('%B')),
            'formatter' => array('class' => 'ListStandard',
                                 'template' => 'tpl_listingbox_productliststd.php',
                                 'params' => array(
                                     'imageListingWidth' => IMAGE_PRODUCT_NEW_LISTING_WIDTH,
                                     'imageListingHeight' => IMAGE_PRODUCT_NEW_LISTING_HEIGHT,
                                     'definePrefix' => 'PRODUCT_NEW_')),
        );
    }
```

### boxTitle

This is optional, but if present will be displayed as the title of the box.

### formatter

This consists of 3 entries

#### class

This is the name of the class that manages the formatting.
The class should be defined in the library/zencart/listingbox/src/formatters directory and should extend the AbstractFormatter
class and implement the FormatterInterface class

e.g. 
`class Columnar extends AbstractFormatter implements FormatterInterface`

#### template

This is the name of the template used to display the listing box. 
It is assumed that the template will be in includes/templates/templates_default/listingboxes or includes/templates/YOUR_TEMPLATE/listingboxes directory.

#### params

the params entry is optional and if set will define parameters used to customize the formatter output.


