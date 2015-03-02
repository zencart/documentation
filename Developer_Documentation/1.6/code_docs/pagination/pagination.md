# Introduction

In previous versions of Zen Cart, pagination has been handled by the split_page_results class. 
This class has lots of problems. 

1. It has a poor API 
2. It's difficult to change the html output
3. It is bound to using sql results. 

For v160 we realised we needed to have a better class structure for doing pagination. 
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

['sqlQueries']['main'] is an sql query string to select the items to be paginated.  
['sqlQueries']['count'] is an sql query string to get the total item count for the items to be paginated.  
['dbConn'] is a queryfactory connection object. e.g. the global $db variable.  

e.g.
 
    $data['sqlQueries']['main'] = "SELECT * FROM " . TABLE_PRODUCTS;  
    $data['sqlQueries']['count'] = "SELECT count(*) as total FROM " . TABLE_PRODUCTS;  
    $data['dbConn'] = $db;  
    
setting the params

     $currentPage = zcRequest::readGet('page', 1); 
     $params['currentPage'] = $currentPage;  
     $params['itemsPerPage'] = 1;
     
then instantiate the adapter

     $ds = new QueryFactory($data, $params);


## Scroller Classes

### Introduction



### Parameters

scrollerLinkParams
maxPageLinks
cmd
linkParams
exclude
pagingVarName
disableZenGetAllGetParams
currentPage
totalPages



