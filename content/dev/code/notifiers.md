 ---
title: Observer/Notifier System 
description: About notifiers and observers
category: code
weight: 10
type: codepage
---

# Introduction

One of the many goals of the Zen Cart project has always been to make it simple for third party developers to add functionality to the core code in an easy and unobtrusive manner. To do this we use the [override system](/user/template/template_overrides/), the [auto inclusion system](/dev/code/inclusion/) and the observer/notifier system.

The observer/notifier system is an implementation of the ["pub-sub" pattern](https://en.wikipedia.org/wiki/Publish–subscribe_pattern)  that was introduced to give developers deep access to core operation without the need to touch any core files at all. Although the implementation was written for an object-oriented code base, it can also be used with procedural code.

At a high level, a developer will do the following: 

- identify an _event_ that they want to monitor, such as when a customer has just successfully logged in.  
- register an observer to be notified when that event occurs.  

If/when that event occurs, the `base` class receives control and looks to see if any registrations exist for the event.  If so, all registered observer-classes are called, and they perform their custom actions.

Here are some 'quick links' to various sections of this documentation:

1. [Issuing Event Notifications](#issuing-event-notifications).  Identifies the mechanism used by _event issuers_ to issue a notification.

2. [Observing Notifications](#observing-notifications). Identifies the mechanisms used by _event observers_ to perform their customizations.

3. [Loading Your Observer Class](#loading-your-observer-class).  Identifies how to load your observer-class so that it can begin its observations.

4. [Advanced Topics](#advanced-topics). This section identifies additional methods that can be used to auto-load an observer-class and create event-specific event-handlers.

    a. [Choosing When to Load an Observer](#choosing-when-to-load-an-observer).

    b. [Auto-loaded Observers](#auto-loaded-observers).

    c. [Event-Specific Update Methods](#event-specific-update-methods).

    d. [Generic Formal Parameter Interpretation](#generic-formal-parameter-interpretation).

5. [Additional Information](#additional-information).  This section has references to additional documentation on the observer/notifier system.


## Issuing Event Notifications

The point of the observer/notifier system is to enable developers to write code that listens for certain events to happen and then perform a customized action for an event.

Events are identified by string-names and are triggered via call to a `notify` method by an _event issuer_.  You can see a [list of notifiers](/dev/code/notifiers_list/) provided by the Zen Cart core for reference. 

**Note**: Plugins (Zen Cart extensions) can also be _event issuers_.

The `notify` method takes the following inputs:

|    Input Name     | Required? | Description                                                  |
| :---------------: | :-------: | ------------------------------------------------------------ |
|     $eventId      |    Yes    | The string 'name' of the event, e.g. `NOTIFIER_CART_ADD_CART_END`. |
|      $param1      |    No     | A read-only variable, the format of which varies by the `$eventId`.  Defaults to an empty array. |
| $param2 - $param9 |    No     | A collection of read-write variables, passed as a reference.  The notification issuer is, essentially, giving permission for an observer to update these variables.  Each variable's format (and presence) varies by the `$eventId` and defaults to `null`. |

#### Class-Based Event Notifications

Within a class that extends the Zen Cart `base` class, e.g.:

```php
class shopping_cart extends base
```

&hellip; events can be issued via the `$this` keyword:

```php
$this->notify('EVENT_NAME');
```

For example, the shopping cart class issues this event after an item has been added to the cart:
```php
$this->notify('NOTIFIER_CART_ADD_CART_END');
```

When a class issues a notification using the `$this` keyword, _all_ **public** class-variables are available for use by a watching observer.  If a class desires to issue a notification without that access, the global `$zco_notifier` can be used to issue that notification.

#### Procedural Event Notifications

In procedural code, functions and classes that don't `extend base`, use the global `$zco_notifier` object to issue events. For example, the `zen_mail` function triggers the following event, which allows a plugin to update the to-be-sent email format:

```php
$zco_notifier->notify('NOTIFY_EMAIL_DETERMINING_EMAIL_FORMAT', $to_email_address, $customers_email_format, $module);
```

## Observing Notifications

To take advantage of notifiers, developers need to write classes to watch for them, i.e. _observe_.  There's even a nice directory, `includes/classes/observers` and `admin/includes/classes/observers`, where developers can put these classes.

There are three *base-class* methods that observers use to provide their custom actions:

| Method Name        | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| [`attach`](#attach) | This method identifies a list of event(s) that the observer-class *is* interested in monitoring. |
| [`update`](#update) | This method is the call-back when an event 'fires'.          |
| [`detach`](#detach) | This method identifies a list of event(s) that the observer-class *is no longer* interested in monitoring. |

#### attach

The `attach`  method is used by an _event observer_ to 'register' to receive control when a specified event (or list of events) occurs.  This method takes two parameters:

1. `$observer`.  Identifies 'who' is requesting to receive control, i.e. `$this` which identifies the current class.  This value is used by the `base` class to create a unique ID associated with the observation request.
2. `$eventIDArray`.  A simple array of event names that the observer-class is 'interested in'.

For example, `/includes/classes/observers/class.products_viewed_counter.php` requests to be notified whenever the event `NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR` is issued.  That event is issued by the various product types' `main_template_vars.php` modules.

``` php
class products_viewed_counter extends base {

  function __construct() {
    $this->attach($this, array('NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR'));
  }
  ...
}
```

#### update

The `update` method is used by an _event observer_ to perform event-specific actions when an event is issued. This method is passed _up to_ 11 parameters:

1. `&$callingClass`. This is a reference to the class in which the event occurred.  If the event is issued by a class other than the `base` (e.g. the `order` or `shopping_cart` class), then this variable can be used to manipulate any ***public*** properties within the calling class. (eg: if the event is called from the `order` class, then inside the observer you would refer to the `order` class's `$this->info` property using `$class->info`)
2. `$eventID`. The name of the event triggered.
3. `$param1`.  _Read-only_ data.  The value is dependent on the `$eventID`.
4. `&$param2` through `&$param9`.  _Updateable_ variables provided by the _event issuer_.  These values, too, are dependent on the `$eventID`.

***Note***: You can also choose to use [event-specific update-methods](#event-specific-update-methods) to handle event-related processing.

Here's the full implementation for `/includes/classes/observers/class.products_viewed_counter.php`:

```php
class products_viewed_counter extends base {

  function __construct() {
    $this->attach($this, array('NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR'));
  }a

  function update(&$class, $eventID, $paramsArray = array())
  {
    if ($eventID == 'NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR')     {
      if (defined('LEGACY_PRODUCTS_VIEWED_COUNTER') && LEGACY_PRODUCTS_VIEWED_COUNTER == 'on')
      {
        global $db;
        $sql = "update " . TABLE_PRODUCTS_DESCRIPTION . "
                set        products_viewed = products_viewed+1
                where      products_id = '" . (int)$paramsArray . "'
                and        language_id = '" . (int)$_SESSION['languages_id'] . "'";
        $res = $db->Execute($sql);
      }
    }
  }

}
```

When the `NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR` event is issued and that constant is defined, the first parameter is _expected to be_ an integer value that identifies the specific product to be updated.  The observer's `update` method, thus, casts the first parameter to an integer value and performs the `products_viewed` update.

#### detach

The `detach` method is used by an _event observer_ to 'un-register' from receiving specified event (or list of events) notifications.  This method takes two parameters:

1. `$observer`.  Identifies 'who' is requesting to receive control, i.e. `$this` which identifies the current class.  This value should be the same as that used to `attach` to the no-longer-wanted event.
2. `$eventIDArray`.  A simple array of event names that the observer-class is no longer 'interested in'.

If, for instance, an observer was interested in the *first* issuance of a given notification, the observer's `update` method, upon receiving that notification, would issue the associated `detach`.

## Loading Your Observer-Class

Next step, loading and creating an 'instance' of your observer-class.  You'll create a file in the Zen Cart `/includes/auto_loaders` (or `/admin/includes/auto_loaders`) sub-directory to perform those tasks.  For the example used above, that file's named `/includes/auto_loaders/config.products_viewed_counter.php`.

The file contains two auto-load statements:

1. An `autoType` of `class` to load your observer's class-file.
2. An `autoType` of `classInstantiate` to create an instance of your observer-class.

The 'load-point', in this example `190` indicates the *relative* position within the auto-loading process at which the auto-load actions are to be performed.  Most observers can safely load at load-point `190` or later (after all the base Zen Cart auto-loaders have completed).  See [Choosing When to Load an Observer](#choosing-when-to-load-an-observer) for some special cases.


```php
if (!defined('IS_ADMIN_FLAG')) {
 die('Illegal Access');
}
$autoLoadConfig[190][] = array('autoType'=>'class',
                              'loadFile'=>'observers/class.products_viewed_counter.php');
$autoLoadConfig[190][] = array('autoType'=>'classInstantiate',
                              'className'=>'products_viewed_counter',
                              'objectName'=>'products_viewed_counter');
```

## Advanced Topics

### Choosing When to Load an Observer

If your observer-class performs actions *prior to* the page-specific loading, e.g. monitoring for cart-related actions, you'll need to make sure that your observer is loaded and instantiated ***before*** any watched-for notification is issued.  In these cases, review the base Zen Cart auto-loader (`[/admin]/includes/auto_loaders/config.core.php`) to identify the load-point required.

### Auto-loaded Observers

If you're developing a plugin that uses an observer-class, in earlier versions of Zen Cart, you would have had to provide ***two*** files in your plugin's distribution to get that class loaded and instantiated:

1. /includes/auto_loaders/config.your_plugin.php
2. /includes/classes/observers/class.your_plugin.php

Starting with Zen Cart v1.5.3, built-in functionality will do the  "heavy lifting" to get your class-file loaded and instantiated, saving you some effort.

Here are the requirements: 

1. The file is in the `/includes/classes/observers` sub-directory and named **auto.**your_plugin.php.  All files in this directory that start with **auto.** will be included (i.e. loaded).
2. The file defines a class named **zcObserver** + the [CamelCased](http://en.wikipedia.org/wiki/CamelCase) filename, e.g. a file named `auto.your_plugin.php` will contain a class named  `zcObserverYourPlugin`.  A myDEBUG\*.log file will be generated if a  properly-named file is loaded, but the class name doesn't conform to  these rules.

Note that this technique will work so  long as your class doesn't have any special requirements on its load  point (auto-loaded classes are loaded at point `175`, after all other  system dependencies are loaded).   

For example, the *Products Viewed Counter* described [above](#update) could provide the same functionality and not need its auto-loader component if the observer-class file was renamed to `/includes/classes/observers/auto.products_viewed_counter.php` and its class name was updated to be `zcObserverProductsViewedCounter.php`.

### Event-Specific Update Methods

Problem: If you register for a number of related events, a single `update` function will be getting different parameters depending on which event fires.

Solution: Your observer-class' `update` method(s) can be customized based on the notification received, since the parameters for a notification depend on the notification received.  So rather than use one `update` method, create separate methods to receive each type of event. 

There are two syntaxes supported for this: 

#### snake_cased event name
This is supported since v1.5.7.

For a notifier named `NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR` you could have a function in your observer class named `notify_product_views_hit_incrementor()` instead of `update()` (and still specify all the same parameters as you would for an `update()` function.

or for older versions, use the camelCased convention described below:

#### camelCased event name

With this alternative syntax, the `update` method's name consists of the word `update` followed by the [CamelCased](http://en.wikipedia.org/wiki/CamelCase) version of the watched-for notification.  For instance, the Products Viewed Counter described [above](#update) could be recoded as an auto-loading, customized-method observer:

```php
class zcObserverProductsViewedCounter extends base 
{
    function __construct() 
    {
        $this->attach($this, array('NOTIFY_PRODUCT_VIEWS_HIT_INCREMENTOR'));
    }

    function updateNotifyProductViewsHitIncrementor(&$class, $eventID, $products_id)
    {
        if (defined('LEGACY_PRODUCTS_VIEWED_COUNTER') && LEGACY_PRODUCTS_VIEWED_COUNTER == 'on') {
            global $db;
            $sql = 
                "UPDATE " . TABLE_PRODUCTS_DESCRIPTION . "
                    SET products_viewed = products_viewed+1
                  WHERE products_id = " . (int)$products_id . "
                    AND language_id = " . (int)$_SESSION['languages_id'] . "
                  LIMIT 1";
             $db->Execute($sql);
         }
    }
}
```

### Generic Formal Parameter Interpretation

One more method for interpretation of parameters is possible when using a 
single method to monitor multiple events.  

The update method may simply "interpret" the parameters in a switch statement, according to the specific eventID being passed. Here's an example from the Edit Orders plugin.  Each of the monitored events uses different parameters, so the formal parameters used in the `update` function declaration are generic.

```
    public function update(&$class, $eventID, $p1, &$p2, &$p3, &$p4, &$p5) 
    {
        switch ($eventID) {
            // -----
            // Issued during the orders-listing sidebar generation, after the upper button-list has been created.
            //
            // $p1 ... Contains the current $oInfo object, which contains the orders-id.
            // $p2 ... A reference to the current $contents array; the NEXT-TO-LAST element has been updated
            //         with the built-in button list.
            //
            case 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS': 
                if (is_object($p1)) {
                    $index_to_update = count($p2) - 2;
                    $p2[$index_to_update]['text'] = $this->addEditOrderButton($p1->orders_id, $p2[$index_to_update]['text']);
                }
                break;
      
            // -----
            // Issued during the orders-listing sidebar generation, after the lower-button-list has been created.
            //
            // $p1 ... Contains the current $oInfo object (could be empty), containing the orders-id.
            // $p2 ... A reference to the current $contents array; the LAST element has been updated
            //         with the built-in button list.
            //
            case 'NOTIFY_ADMIN_ORDERS_MENU_BUTTONS_END':
                if (is_object($p1) && count($p2) > 0) {
                    $index_to_update = count($p2) - 1;
                    $p2[$index_to_update]['text'] = $this->addEditOrderButton($p1->orders_id, $p2[$index_to_update]['text']);
                }
                break;
                
            // -----
            // Issued during the orders-listing generation for each order, gives us a chance to add the icon to
            // quickly edit the associated order.
            //
            // $p1 ... An empty array
            // $p2 ... A reference to the current order's database fields array.
            // $p3 ... A reference to the $show_difference variable, unused by this processing.
            // $p4 ... A reference to the $extra_action_icons variable, which will be augmented with an icon
            //         linking to this order's EO processing.
            //
            case 'NOTIFY_ADMIN_ORDERS_SHOW_ORDER_DIFFERENCE':
                $p4 .= $this->createEditOrdersLink($p2['orders_id'], zen_image(DIR_WS_IMAGES . EO_BUTTON_ICON_DETAILS, EO_ICON_DETAILS), EO_ZC156_FA_ICON, false);
                break; 
```

Some developers believe this method should not be used since it is less self-documenting than prior methods.  Others prefer it for its compactness of expression when compared to the more long-winded camelCase.

## Additional Information

### Event Aliasing 

Sometimes notifier names are changed (because of a typo, for example, or to make them more self-documenting).  When this happens, rather than just remove the old notifier, the recommended practice since Zen Cart 1.5.7 has been to alias the old name.  This way, older code which uses the old notifier name will still work. 

### Plugins which support Notifier Use 

Some plugins which can be helpful during development when using notifiers include:

* [Watching Observers](https://www.zen-cart.com/downloads.php?do=file&id=2273)
* [Zen Cart Notifier Report](https://www.zen-cart.com/downloads.php?do=file&id=2260)

### Information about Notifiers 
* A [list of notifiers](/dev/code/notifiers_list) is provided for the current Zen Cart release. 
* The output of the [Zen Cart Notifier Report](/dev/code/notifier_report/) is provided on the docs site for easy reference by developers. 
