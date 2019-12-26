# Introduction

In previous versions of Zen Cart, pagination has been handled by the split_page_results class. 
This class has lots of problems. 

1. It has a poor API 
2. It's difficult to change the html output
3. It is bound to using sql results. 

For v2, we realised we needed to have a better class structure for doing pagination. 
The new structure defines 2 sets of objects. 

`Adapters,` which are responsible for producing the lists of items that might appear in a paginated view.

`Scrollers` which define how the actual link lists for a paginated result set are built.

 
## Adapter Classes

### Introduction 

Adapter classes are meant to return a list of items that will be displayed in the pagination results/template.
In the old split_page_results_class, the only way to get this list of items was to use an sql query. 
However there might be other ways we want to generate that list. 

e.g. 
Using queryFactory to take an sql query string
Using a queryFactory resultset
Using an array generated either from queryFactory  or from some other db layer (pdo, doctrine, noSql etc)

The Adapter class expects us to pass a $data array and a $params array.

The $data array, is dependant on the concrete adapter class, but can generally be thought of as providing information that
 will create a result set. 
 
The $params array is fluid, however is expected to provide at least 2 pieces of information. 

The currentPage and the itemsPerPage. 
If these are not passed in the $params array, defaults will be set


### Interface

Adapter Classes implement a simple interface.

getResultList which returns a list of items, based on $data/$param settings.
 
getTotalItemCount which returns the total number of items. regardless of limits.



### Parameters 

currentPage **required**  
itemsPerPage **required**

### Results

Adapter Classes return a simple array via the getResults() method. 
The array consists of the following.

>
totalItemCount  
currentItem  
itemsPerPage  
resultList  
totalPages  

### Example using the QueryFactory Adapter

The QueryFactory adapter class expects its data array to be formatted as follows 

['mainSql'] is an sql query string to select the items to be paginated.  
['count'] is an sql query string to get the total item count for the items to be paginated.  
['dbConn'] is a queryfactory connection object. e.g. the global $db variable.  

e.g.
 
    $data['sqlQueries']['main'] = "SELECT * FROM " . TABLE_PRODUCTS;  
    $data['sqlQueries']['count'] = "SELECT count(*) as total FROM " . TABLE_PRODUCTS;  
    $data['dbConn'] = $db;  
    
setting the params

     $currentPage = $zcRequest->readGet('page', 1); 
     $params['currentPage'] = $currentPage;  
     $params['itemsPerPage'] = 10;
     
then instantiate the adapter

     $ds = new QueryFactory($data, $params);

results can then be gotten using 

     $results = $ds->getResults()
     
     
## Scroller Classes

### Introduction

There are lots of different ways to show pagination controls in a template.  
Legacy Zen Cart has one way of doing it,  
Google has another way of doing it. 

Scroller classes allow for different methods of building the Link list that a template will render.

### Interface

Scroller classes need only provide a public process method.

### Parameters

#### pagingVarName 

This is the name of the URL GET parameter that denotes the current page.
e.g. localhost.com/main_page=list?page=1
by default his is set to `page`

####cmd 

cmd represents the current page controller. 
e.g. in catalog where we have a url like 
localhost.com/main_page=reviews 
cmd would be `reviews`


#### scrollerLinkParams (optional)

When building the href links for scroller outout, these params will be added to the link.
Should take the form of a string like `linkParam1=value1&LinkParam2=value2`

#### maxPageLinks 


#### exclude 

Generally, page links will use the zen_get_all_get_params() function to add GET params to the paging links,
you can add GET params to exclude using this array;

#### disableZenGetAllGetParams
 
Don't use zen_get_all_get_params to build paging links.
 
#### currentPage 

An integer value for the current page being displayed, will default to 1

#### totalPages 

The total number of pages that the Adapter class returned.

### Results

The public process method should create a results array containing values to be used in the paginator output template.
The format of this array is flexible, being dependant on how you want the view output to be rendered, but a look at the 
standard scroller should provide some hints as to the general values that should be returned.


        $results['linkList']
        $results['pagingVarName']
        $results['hasItems']
        $results['nextPage']
        $results['totalItems']
        $results['prevPage']
        $results['fromItem']
        $results['toItem']
        $results['flagHasPrevious']
        $results['flagHasNext']
        $results['previousLink']
        $results['nextLink']


### Example using the Standard Scroller

        $params = array('pagingVarName'=>'page', 'scrollerLinkParams'=>'', 'itemsPerPage'=>'10', 'currentItem'=>'1', 'currentPage'=>'1', 'maxPageLinks'=>'10', 'cmd'=>'countries');
        $scroller = new Standard($ds, $params);
        $dsr = $scroller->getResults();

How you pass the $dsr results to the template is up to you. 
Remember, templates currently will need to have variables in the Global scope. 
So you may need to do something like 

$GLOBALS['tplVars']['paginator'] = $dsr;

and you can then access the results in the template 
i.e. 

    <?php if ($tplVars['paginator']['flagHasPrevious']) { ?>
