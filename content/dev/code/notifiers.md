---
title: Notifiers and Observers - About
description: About Zen Cart Notifiers and Observers 
category: code
weight: 10
---

### Introduction

One of the many goals of the Zen Cart project has always been to make it easier for third party developers to add functionality to the core code in an easy and unobtrusive manner. To do this we have in the past relied on the override and auto inclusion systems. However these still do not give developers an easy method of hooking into many areas of core code, without 'hacking' core files themselves.

The observer/notifier system was introduced to give developers unprecedented access to core code, without the need to touch any core files at all. Although ostensibly written for an object-oriented code base, we will see later how it can be used with general procedural code as well.

### Extending All Classes

In order to implement the observer/notifier system, some structural changes have been made to Zen Cart. Firstly two new classes have been introduced: the base class (`class.base.php`) and the notifier class (`class.notifier.php`).

The base class contains the code that is used to implement the observer/notifier system. However to make it effective all other Zen Cart classes now have to be declared as children of the base class. You will see this if you look at the source of any of the Zen Cart classes.

<pre>  class currencies extends base {
</pre>

The notifier class will be discussed later, when we look at extending the observer/notifier system (ONS) into procedural code.

### Notifiers: Big Brother is watching

So, what is all the fuss about?

The point of the ONS is that developers can write code that wait for certain events to happen, and then when they do, have their own code executed.

So, how are events defined, where are they triggered?

Events are triggered by code added to the core for v1.3 (with more to be added over time). In any class that wants to notify of an event happening we have added:

<pre> $this->notify('EVENT_NAME');
</pre>

An example would probably help here:

In the shopping cart class after an item has been added to the cart this event is triggered:

<pre> $this->notify('NOTIFIER_CART_ADD_CART_END');
</pre>

There are many other events that have notifiers in Zen Cart v1.3 and newer; for a list [see here](/dev/code_notifier_list).

All of this notifying is all well and good, but how does this help developers?

### Observe and Prosper

To take advantage of notifiers, developers need to write some code to watch for them. Observers need to be written as a class. There's even a nice directory, `includes/classes/observers`, where developers can put these classes.

Lets take an example. Using the notifier mentioned above (`NOTIFIER_CART_ADD_CART_END`), how would I write a class that watched for that event?

```
<?php
 class myObserver extends base {
   function __construct() {
     $this->attach($this, array('NOTIFIER_CART_ADD_CART_END'));
   }
...
 }
```

As you can see we have defined a new class called myObserver and in the constructor function for that class (function myObserver) have attached this myObserver class to the event `NOTIFIER_CART_ADD_CART_END`.

"Fine," I hear you saying, "but how do I actually do anything useful?"

Ok, good question. Whenever an event occurs, the base class looks to see if any other observer class is watching that event. If it is, the base class executes a method in that observer class. Remember the `$this->notify('EVENT_NAME')` from above? Well, when that event occurs, the base class calls the update method of all observers. Lets see some more code:

```
class myObserver extends base {
   function __construct() {
     $this->attach($this, array('NOTIFIER_CART_ADD_CART_END'));
   }
   function update(&$callingClass, $notifier, $paramsArray) {
     ... do some stuff
   }
 }
```

Now, whenever the `NOTIFIER_CART_ADD_CART_END` occurs, our `myObserver::update` method will be executed. Note that `attach()` may be called as a method of whatever class you want to listen to (`$_SESSION['cart']`, in this case) or by the internal class variable $this. Both are available since each are part of the class base, where the attach method resides.

Some notes about the parameters...the attach method has two parameters:

*   &$observer - Reference to the observer class, used to generated a unique ID for the new listener
*   $eventIDArray - An array of notifiers that this observer is listening for

The update method is passed three parameters. These are:

*   &$callingClass - This is a reference to the class in which the event occurred, allowing you access to that class's variables
*   $notifier - The name of the notifier that triggered the update (It is quite possible to observe more than one notifier)
*   $paramsArray - Not Used Yet (for future)

NB! The observer/notifier system is written for an OOP-based application, as the observer expects to attach to a class that has notifiers within its methods. However a lot of the code within Zen Cart is still procedural in nature and not contained within a class.

To work around this, we added the 'stub' notifier class. So if you want to create an observer for a notifier that lies within procedural code (like in page headers) you should add the notifier into your myObserver class like this:

```
class myObserver extends base {
   function __construct() {
     global $zco_notifier;
     $zco_notifier->attach($this, array('NOTIFY_HEADER_END_CHECKOUT_CONFIRMATION'));
   }
```

### Including observers into your code

Please note that the `includes/classes/observers` directory is not an autoload directory, so you will need to arrange for `application_top.php` to autoload your observer class as was described above (add a new `config.xxxxx.php` file in the `auto_loaders` folder, etc). Let's assume you are using the freeProduct class (see the example below), and you have saved this in `includes/classes/observers/class.freeProduct.php`.

You now need to arrange for this class to be loaded and instantiated. To do this you need to use the `application_top.php` autoload system.

In `includes/auto_loaders` create a file called `config.freeProduct.php` containing

```
$autoLoadConfig[10][] = array('autoType'=>'class',
                              'loadFile'=>'observers/class.freeProduct.php');
$autoLoadConfig[90][] = array('autoType'=>'classInstantiate',
                              'className'=>'freeProduct',
                              'objectName'=>'freeProduct');
```

Note: 10 has been chosen to cause the observer class to be loaded before the session is started. Note: 90 has been chosen as the offset since the observer needs to attach to the `$_SESSION['cart']` class (see the freeProduct example below), which is instantiated at offset 80.

To tie this all together, let's look at a real world example.

### A Real World Example

One of the most-often requested features is the ability for the store to automatically add a free gift to the Shopping Cart if the customer spends more than a certain amount.

The code has to be intelligent: it has to not only add the free gift when the shopper spends over a certain amount, but also remove the gift if the user changes the contents of the shopping cart, such that the total falls below the threshold.

Traditionally, although the code for this is not particularly difficult, it would have meant 'hacking' the core shoppingCart class in a number of places. With the ONS, this can be achieved with one very small custom class and absolutely no hacking whatsoever.

Here's the code.

```
<?php
/**
 * Observer class used to add a free product to the cart if the user spends more than $x
 *
 */
class freeProduct extends base {
  /**
   * The threshold amount the customer needs to spend.
   * 
   * Note this is defined in the shops base currency, and so works with multi currency shops
   *
   * @var decimal
   */
  var $freeAmount = 50;
  /**
   * The id of the free product.
   * 
   * Note. This must be a true free product. e.g. price = 0 Also make sure that if you don't want the customer
   * to be charged shipping on this, that you have it set correctly.
   *
   * @var integer
   */
  var $freeProductID = 57;
  /**
   * constructor method
   * 
   * Attaches our class to the $_SESSION['cart'] class and watches for 2 notifier events.
   */
  function __construct() {
    $_SESSION['cart']->attach($this, array('NOTIFIER_CART_ADD_CART_END', 'NOTIFIER_CART_REMOVE_END'));
  }
  /**
   * Update Method
   * 
   * Called by observed class when any of our notifiable events occur
   *
   * @param object $class
   * @param string $eventID
   */
  function update(&$class, $eventID, $paramsArray = array()) {

  if ($eventID == 'NOTIFIER_CART_REMOVE_END' && (isset($_SESSION['freeProductInCart']) && $_SESSION['freeProductInCart'] == TRUE ))
  {
    if (!$_SESSION['cart']->in_cart($this->freeProductID))
    {
      $_SESSION['userRemovedFreeProduct'] = TRUE;
    }
  }

  if (!isset($_SESSION['userRemovedFreeProduct']) || $_SESSION['userRemovedFreeProduct'] != TRUE) 
  {
    if ($_SESSION['cart']->show_total() >= $this->freeAmount && !$_SESSION['cart']->in_cart($this->freeProductID) )   
    {
      $_SESSION['cart']->add_cart($this->freeProductID);
      $_SESSION['freeProductInCart'] = TRUE;  
    }
  }

  if ($_SESSION['cart']->show_total() < $this->freeAmount && $_SESSION['cart']->in_cart($this->freeProductID) ) 
  {
    $_SESSION['cart']->remove($this->freeProductID);
  }

  if ($_SESSION['cart']->in_cart($this->freeProductID)) 
  {
    $_SESSION['cart']->contents[$this->freeProductID]['qty'] = 1;
  }

  }  
}
?>
```

A couple notes:

First, I have set the options for the system in the class itself. This is obviously a bad idea, and it would be much better to have an admin module to set these options.

Second, notice that we are actually watching for two events in the one class.

```
$_SESSION['cart']->attach($this, array('NOTIFIER_CART_ADD_CART_END', 'NOTIFIER_CART_REMOVE_END'));
```

so we are watching for the `NOTIFIER_CART_ADD_CART_END` and `NOTIFIER_CART_REMOVE_END` of the shopping_cart class.

The update class is extremely simple but in its simplicity manages to do all the work we require of it. It first tests to see if the total in the cart is over the threshold and, if it hasn't already, adds the free product to the cart.

It then tests to see if the cart total has dropped below the threshold and, if the free product is in the cart, removes it.

Now that was cool, how about something a little more difficult.

### Another Real World Example

Again we return to the Shopping Cart and promotions. Another oft-requested feature is the BOGOF promotion, or Buy One Get One Free. This is a little more difficult to achieve than our previous example, as there is some manipulation needed of the cart totals. However as you will see it is still pretty much a breeze.

```
<?php
/**
 * Observer class used apply a Buy One Get One Free(bogof) algorithm to the cart
 *
 */
class myBogof extends base {
  /**
   * an array of ids of products that can be BOGOF.
   *
   * @var array
   */
  var $bogofsArray = array(10,4); //Under Siege2-Dark Territory & The replacement Killers
  /**
   * Integer number of bogofs allowed per product
   * 
   * For example if I add 4 items of product 10, that would suggest that I pay for 2 and get the other 2 free.
   * however you may want to restrict the customer to only getting 1 free regardless of the actual quantity
   *
   * @var integer
   */
  var $bogofsAllowed = 1;
  /**
   * constructor method
   * 
   * Watches for 1 notifier event, triggered from the shopping cart class.
   */
  function __construct() {
    $this->attach($this, array('NOTIFIER_CART_SHOW_TOTAL_END'));
  }
  /**
   * Update Method
   * 
   * Called by observed class when any of our notifiable events occur
   * 
   * This is a bit of a hack, but it works. 
   * First we loop through each product in the bogof Array and see if that product is in the cart.
   * Then we calculate the number of free items. As it is buy one get one free, the number of free items
   * is equal to the total quantity of an item/2.
   * Then we have to hack a bit (would be nice if there was a single cart method to return a product's in-cart price)
   * We loop thru the cart until we find the bogof item, get its final price, calculate the saving
   * and adjust the cart total accordingly.
   *
   * @param object $class
   * @param string $eventID
   */
  function update(&$class, $eventID) {
    $cost_saving = 0;
    $products = $_SESSION['cart']->get_products();
    foreach ($this->bogofsArray as $bogofItem) {
      if ($_SESSION['cart']->in_cart($bogofItem)) {
        if (isset($_SESSION['cart']->contents[$bogofItem]['qty']) && $_SESSION['cart']->contents[$bogofItem]['qty'] > 1) {
          $numBogofs = floor($_SESSION['cart']->contents[$bogofItem]['qty'] / 2);
          if ($numBogofs > $this->bogofsAllowed) $numBogofs = $this->bogofsAllowed;
          if ($numBogofs > 0) {
            for ($i=0, $n=sizeof($products); $i<$n; $i++) {
              if ($products[$i]['id'] == $bogofItem) {
                $final_price = $products[$i]['final_price'];
                break;
              }
            }
            $cost_saving .= $final_price * $numBogofs;
          }
        }
      }
    }
    $_SESSION['cart']->total -= $cost_saving;
  }
}
?>
```

NB: There are still some weaknesses here...

First although the adjust total is correctly shown on the shopping cart page and sidebox, the line total is not adjusted.

Secondly this will probably produce a confusing output at checkout.

Third: Have not tested for tax compliance yet ( @TODO )

### Mods which support Notifier Use 
A number of mods are provided which can be helpful during development when using notifiers: 

* [Zen Cart Notifier Report](https://www.zen-cart.com/downloads.php?do=file&id=2260)
* [Zen Cart Notifier Trace](https://www.zen-cart.com/downloads.php?do=file&id=1114)

### List of Notifiers 
A [list of notifiers](/dev/code/notifiers_list) is provided for the current release. 

