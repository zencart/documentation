# Formatter Classes

Formatter classes take the ordered list of items that are produced by the listingBox/queryBuilder and format them into an array that an output template can use.

## Defining Formatters

Formatters are defined as part of the $this->outputLayout definition in the initQueryAndOutput method of a listing box class.

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
It is assumed that the template will be in includes/templates/templates_default/listingboxes or includes/templates/YOURTEMPLATE/listingboxes directory.

#### params

The params entry is optional and if set will define parameters used to customize the formatter output.

## Formatter Classes

As mentioned earlier formatter classes should extend the AbstractFormatter class and implement the FormatterInterface class.

e.g. 

```php
class Columnar extends AbstractFormatter implements FormatterInterface
{
    /**
     *
     */
    public function format()
    {
        $items = $this->itemList;
        $formatterParams = $this->outputLayout['formatter']['params'];
        $columnCount = $formatterParams['columnCount'];
        $row = 0;
        $col = 0;
        $listBoxContents = array();
        if (count($items) == 0) {
            return;
        }
        $col_width = floor(100 / $columnCount);
        if (count($items) < $columnCount || $columnCount == 0) {
            $col_width = floor(100 / count($items));
        }
        foreach ($items as $item) {
            $item ['colWidth'] = $col_width;
            $item ['useImage'] = ($item ['products_image'] != '' || PRODUCTS_IMAGE_NO_IMAGE_STATUS != 0) ? true : false;
            $listBoxContents [$row] [$col] = $item;
            $col++;
            if ($col > ($columnCount - 1)) {
                $col = 0;
                $row++;
            }
        }
        $this->formattedResults = $listBoxContents;
    }
}
```

Note also that the formatter class takes the unformatted array `$this->itemList` and after formatting assigns it to `$this->formattedResults`.

