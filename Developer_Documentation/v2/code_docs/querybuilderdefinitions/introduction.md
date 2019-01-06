Introduction
============

ListingQueryAndOutput are lists of product items that appear in the main content area of a Zen Cart page. Examples are the Specials/Feature/new and upcoming product lists that appear mainly on the home page and sometimes on other pages as well.

In previous versions of Zen Cart each listing box had its own code that used hard coded queries and fixed templates to show the output. This has proven inflexible and makes it difficult for 3rd party contributions to add or alter these, without changing core code or templates.

To address this, Zen Cart v2 includes a Class based system for building listing box output  and simpler more designer friendly templates for displaying the results.

The system contains 4 main parts.

1. Classes that allow you to define the  products will be displayed, and how they will be displayed. This uses an array to define the query that is used to find products, and an array to manage the output format.
2. Decorator classes that take the items returned from above and filter/re-order those items in preparation for display.
3. Formatter classes that take the final results and prepare an array of the results ready for a template.
4. Output templates. These may be overridden to use 3rd party templates.

 
