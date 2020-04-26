---
title: Notifiers and Observers - About
description: About Zen Cart Notifiers and Observers 
category: code
weight: 10
---

### Introduction

One of the many goals of the Zen Cart project has always been to make it simple for third party developers to add functionality to the core code in an easy and unobtrusive manner. To do this we use the [override system](/user/template/template_overrides/), the auto inclusion system, and the observer-notifier system.

The observer/notifier system is an implementation of the ["pub-sub" pattern](https://en.wikipedia.org/wiki/Publish–subscribe_pattern).  It was introduced to give developers deep access to core operation, without the need to touch any core files at all. Although it was written for an object-oriented code base, it can be used with procedural code as well.

### Extending All Classes

In order to use notifiers in a class, you will need to make that class extend the `base` class. eg:

<pre>  class currencies extends base {
</pre>


### Notifiers: Big Brother is watching

The point of the observer/notifier system is to permit developers to write code that listens for certain events to happen, and then when they do, have their own code executed.

Events are simply mnemonic strings.  You can see a 
[list of notifiers](/dev/code/notifiers_list) for reference.

Events are triggered by calling `$this->notify` in any class that `extends base`:

<pre> $this->notify('EVENT_NAME');
</pre>

Example: In the shopping cart class after an item has been added to the cart this event is triggered:

<pre> $this->notify('NOTIFIER_CART_ADD_CART_END');
</pre>

In procedural code (or outside of a class that `extends base`) use the global `$zco_notifier` object. For example, inside the `zen_mail` function this event is triggered, which allows a plugin to update the sent email format:

<pre>  $zco_notifier->notify('NOTIFY_EMAIL_DETERMINING_EMAIL_FORMAT', $to_email_address, $customers_email_format, $module);
</pre>

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
*   $param1 - immutable data. Could be an array or string or integer. 
*   &$param2, &$param3, &$param4 ... up to &$param9 -- mutable variables that can be directly updated by the observer code

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
   * ALERT: There are still some things missing in this example:
   * - although the adjust total is correctly shown on the shopping cart page and sidebox, the line total is not adjusted.
   * - this will probably produce a confusing output at checkout.
   * - needs work on updating taxes as well
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
```

### Using Observers To Interact With And Update Passed Parameters Directly

The real power of using Observer classes to respond to Notifier hooks is in directly updating passed parameters in real time based on the custom logic offered by the observer class.

For this there are two requirements: pass the variable to the notifier hook, and receive that variable by-reference in the observer function.

In this example we pass 3 variables: `$to_email_address`, `$customers_email_format`, and `$module`.
The first parameter is always immutable, unchangeable. The 2nd-through-9th parameter can be changed directly by the observer when received-by-reference (see below).

```
$zco_notifier->notify('NOTIFY_EMAIL_DETERMINING_EMAIL_FORMAT', $to_email_address, $customers_email_format, $module);

```

Then in the observer class we attach to this notifier in the constructor, and then receive those variables in the `update()` method (note the `&` which "receives the variable by reference" so it can be updated in real-time):

```
class emailSpamFilter extends base
{
  public function __construct {
    $this->attach($this, ['NOTIFY_EMAIL_DETERMINING_EMAIL_FORMAT']);
  }
  
  public function update(&$class, $event, $to_email_address, &$customers_email_format, &$module) {
    // abort sending to any '.ru' addresses
    if (substr($to_email_address, -3) == '.ru') {
      $customers_email_format = 'NONE';
    }
  }
}
```


### Listening to Multiple Notifier Hooks In A Single Observer Class


An observer can listen to multiple notifier hooks, by simply adding more listener names to the array in the constructor. 

But this introduces a problem: how does the `update()` method know which event it's responding to?

There are two ways to handle this situation: custom `updateXYZ()` functions, or using a `switch` statement to handle each event based on the event name. Each has its pros and cons.

The recommended way is to use a custom `update()` method name, conforming to the pattern of: `updateListenerNameInCamelCase()`. You'll notice that this way the variables passed in the notifier call can be intuitively named within the function signature, and when they are received-by-reference any updates to them will be immediately passed back to the calling code, without need for reaching to global variables.

Example:

```
class exampleObserverClass extends base
{
  public function __construct {
    $this->attach($this, ['NOTIFY_LISTENER_NUMBER_ONE', 'NOTIFY_LISTENER_NUMBER_TWO']);
  }
  
  public function updateNotifyListenerNumberOne(&$class, $event, $price, &$data, &$purchase_order, &$shipping_cost) {
    if ($price > 5000) {
      // set status because threshold was met
      $purchase_order['threshold_approved'] = true;
      // free shipping
      $shipping_cost = 0;
    }
  }

  public function updateNotifyListenerNumberOne(&$class, $event, $payment_details, &$customer_email, &$order_data) {
    if ($payment_details['status'] == 'failed') {
      $order_data['payment_status'] = 'failed';
    }
  }
}
```

Or, you could loop through the list of attached notifiers, and respond via one great big `switch` statement, with generic variable names:

```
class exampleObserverClass extends base
{
  public function __construct {
    $this->attach($this, ['NOTIFY_LISTENER_NUMBER_ONE', 'NOTIFY_LISTENER_NUMBER_TWO']);
  }
  
  public function update(&$class, $event, $param1, &$param2, &$param3, &$param4, &$param5)
  {
      switch $event {
        case 'NOTIFY_LISTENER_NUMBER_ONE':
            if ($param1 > 5000) {
                // set status because threshold was met
                $param3['threshold_approved'] = true;
                // free shipping
                $param4 = 0;
            }
            break;

        case 'NOTIFY_LISTENER_NUMBER_TWO':
            if ($param1['status'] == 'failed') {
                $param3['payment_status'] = 'failed';
            }
            break;
      }
  }
}
```

### Plugins which support Notifier Use 
Some plugins which can be helpful during development when using notifiers include:

* [Zen Cart Notifier Report](https://www.zen-cart.com/downloads.php?do=file&id=2260)
* [Zen Cart Notifier Trace](https://www.zen-cart.com/downloads.php?do=file&id=1114)

### Information about Notifiers 
* A [list of notifiers](/dev/code/notifiers_list) is provided for the current release. 
* The [output of the notifier report](/dev/code/notifier_report/) is provided on the docs site for easy reference by developers. 
