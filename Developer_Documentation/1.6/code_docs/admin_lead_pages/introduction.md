Introduction
============

The Zen Cart Administration Interface contains a number of pages that are used to manage a simple list of items. Examples are the admin->Locations/Taxes/Countries page, the admin->Locations/Taxes/Zones page and many others.

What is common amongst these pages is that they initially show a paginated list of entries, and then allow you to add new entries/edit an existing entry and delete entries.

The current pages that manage these lists have a number of problems. They are difficult to create easily, they are almost impossible to customize using add-ons and the code is usually quite messy, with php code interspersed with output HTML.

The new style admin LEAD pages are completely object oriented. Code is separate from the output templates. They are easy to create, in fact a lot of LEAD pages can be created by simply defining some simple array structures.

The LEAD pages also integrate a simple filtering system, that allows the admin user to select a subset of the items in the list.

By the way LEAD stands for List/Edit/Add/Delete

LEAD pages leverage a number of new classes/structures added to v160.

Admin Action Controllers define a new way of writing admin pages, where the code is separated from the template.
 
Listing Box classes that allow for complex querying of the database using a structured array.
  
Service classes that separate domain specific concerns from the controllers.

We will show examples of using all three of the above classes in the documentation.

LEAD Controllers
================

New pages that are being written for Zen Cart admin should use the new controller classes. Documentation for controller classes can be found here.

Generally the controller classes for Admin LEAD pages are very simple. 

e.g. 

<?php
/**
 * @copyright Copyright 2003-2016 Zen Cart Development Team
 * @license http://www.zen-cart.com/license/2_0.txt GNU Public License V2.0
 * @version $Id:  New in v1.6.0 $
 */
namespace ZenCart\Controllers;

/**
 * Class Countries
 * @package ZenCart\Controllers
 */
class Countries extends AbstractLeadController
{
}


There may be reasons to override methods in the AbstractLeadController and examples will be given later.

ListingBox Classes
==================

The main workhorse of the LEAD pages are defined as ListingBox classes.
More information about ListingBox classes can be found here.


