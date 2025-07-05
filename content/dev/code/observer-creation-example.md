 ---
title: Creating an Observer Class (HOW-TO example)
description: Example Observer to send a specialized additional email during Create Account
category: code
weight: 10
type: codepage
---

# Let's Discover How To Create An Observer Class, Step By Step

## Task:
- Storeowner wants to send the customer an email with a unique code when the customer creates an account.
- The code pattern is "ABC00001", where ABC is fixed text, and 00001 is the customer number, with leading zeros up to exactly 5 digits.
- There is no need to build a database of already-issued codes, since the customer ID number is already unique per customer.
- (This example was built based on v1.5.0 code, so adheres to some early basic implementation approaches.)

## The thinking and coding process
First, since this must happen during account-creation, it makes sense to consider looking at the `/includes/modules/create_account.php` script which handles those activities.

Since the intention is to see whether an Observer class can be used for this, I started by scanning the file for any notifier hooks. 
These can be identified in either of two ways: calls to `$zco_notifier->notify()` for procedural code or `$this->notify()` from inside any class method.

We want a notifier point that fires sometime after a customer has submitted their user information and it's been validated.

So, at the end of the validation code there's this one:
```php
    $zco_notifier->notify('NOTIFY_FAILURE_DURING_CREATE_ACCOUNT');
```
... but we're not interested in a "failure" case, so we keep looking:

The next one is this:
```php
    $zco_notifier->notify('NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD', array_merge(array('customer_id' => $_SESSION['customer_id']), $sql_data_array));
```

And, looking closely at the code immediately above it, we see that that part of the code has just finished building the new customer data for the database, 
inserted that record, and set the `customer ID` into the session, effectively logging them in. This is perfect! 
And what's even better is that the `$sql_data_array` has also been passed, so we can make use of that to customize the email with the customer's name and email address.

So, now we start with creating an observer class. We start with the basic structure:
```php
<?php
/**
 * Observer class for sending an extra email during customer-creation/welcome process
 */
class send_extra_email_at_welcome extends base {

  function __construct() 
  {
  }

  function update(&$class, $eventID, $paramsArray = array())
  {
  }
 }
```
You'll see here that we've given the class a name of `send_extra_email_at_welcome`. 
This name will be used later in the auto_loader to activate this observer class. The name itself just needs to be unique from any other class used in the store.

Next we need to set up the constructor to watch the `NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD` hook we identified earlier. 
Since the notifier hook is activated via a public/global `$zco_notifier` call, we set the observer up to attach to that `$zco_notifier->notify()` call:
```php
  function __construct() 
  {
    global $zco_notifier;
    $zco_notifier->attach($this, array('NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD'));
  }
```
We have a few main tasks to perform when this notifier hook is called:
a) create a formatted "code" based on the customer number
b) assemble email text with the code
c) send the email

Let's look at these one at a time:

a) create the formatted code from the customer number. We'll use the PHP function str_pad() to add enough zeros to make a 5-digit value from the customer number:
```php
    /**
     * Here we take the customer number, and add enough zeros to the left of it to make it be 5 digits long.
     */
    $code = str_pad($_SESSION['customer_id'],5,'0',STR_PAD_LEFT); 
```
and then add the ABC prefix to the beginning of it:
```php
    /**
     * Then the 'ABC' prefix is added to it:
     */
    $code = 'ABC' . $code; 
```

b) Put together some email text, using the code. The first line here is the plain-text content. The $html_msg array will contain the same content, but formatted as HTML, in case the customer has opted to receive html-formatted messages in their preferences during signup.
```php
    $email_text = 'Here is your unique code: ' . $code;
    $html_msg['EMAIL_MESSAGE_HTML'] .= nl2br($email_text); 
```
We'll need a subject line for the email:
```php
    $email_subject = 'Your unique customer code!';
    $html_msg['EMAIL_SUBJECT'] = $email_subject; 
```
c) To send the email, we need to get the customer's email address. The call to $zco_notifier->notify() included some extra parameters, which show up in this observer class via the $paramsArray variable:
```php
    $customer_email_address = $paramsArray['customers_email_address']; 
```
Similarly, in this case we happen to also have access to the customer's firstname/lastname, based on whatever they supplied during signup. Here we concatenate both values into a single string:
```php
    $customer_name = $paramsArray['customers_firstname'] . ' ' . $paramsArray['customers_lastname']; 
```
And now we send the email, using all the data we've prepared:
```php
    zen_mail($customer_name, $customer_email_address, $email_subject, $email_text, STORE_NAME, EMAIL_FROM, $html_msg); 
```

### Finished Code
When we put it all together, the finished code looks like this:
```php
<?php
/**
 * Observer class for sending an extra email during customer-creation/welcome process
 */
class send_extra_email_at_welcome extends base {

  function __construct() 
  {
    global $zco_notifier;
    $zco_notifier->attach($this, array('NOTIFY_MODULE_CREATE_ACCOUNT_ADDED_CUSTOMER_RECORD'));
  }

  function update(&$class, $eventID, $paramsArray = array())
  {
    /**
     * Here we take the customer number, and add enough zeros to the left of it to make it be 5 digits long.
     */
    $code = str_pad($_SESSION['customer_id'],5,'0',STR_PAD_LEFT);
    /**
     * Then the 'ABC' prefix is added to it:
     */
    $code = 'ABC' . $code;
    /**
     * Now build and send the email to the customer
     */
    $email_text = 'Here is your unique code: ' . $code;
    $html_msg['EMAIL_MESSAGE_HTML'] .= nl2br($email_text);
    
    $email_subject = 'Your unique customer code!';
    $html_msg['EMAIL_SUBJECT'] = $email_subject;

    $customer_name = $paramsArray['customers_firstname'] . ' ' . $paramsArray['customers_lastname'];
    $customer_email_address = $paramsArray['customers_email_address'];

    zen_mail($customer_name, $customer_email_address, $email_subject, $email_text, STORE_NAME, EMAIL_FROM, $html_msg);
  }
}
```
We'll store this code into a new file, named `/includes/classes/observers/class.send_extra_email_at_welcome.php`

### Enabling The Observer
Finally, to turn the whole thing on, we add the auto_loader code to tell Zen Cart to load the observer class and instantiate it. 
The file will be uploaded to: `/includes/auto_loaders/config.send_extra_email_at_welcome.php`:
```php
<?php
$autoLoadConfig[190][] = array('autoType'=>'class',
                              'loadFile'=>'observers/class.send_extra_email_at_welcome.php');
$autoLoadConfig[190][] = array('autoType'=>'classInstantiate',
                              'className'=>'send_extra_email_at_welcome',
                              'objectName'=>'send_extra_email_at_welcome');
```
The value of `190` is used to essentially process all of this at the end of the normal autoloader stack.
The load file points to the class file created earlier. 
And the className matches the class name in the class file we made, and the objectName is basically the instantiation object built to fire the observer when appropriate ... it usually is just the same as the className.

That's it. With both of those files in place, when the customer creates a new account, they will receive an extra email (in addition to the normal Welcome email) in which they are told their unique customer code.

### Other Considerations

#### What about making it multi-language capable?
To do this, we must change the language text into defined constants.
So, we'll take these two lines:

```php
    $email_text = 'Here is your unique code: ' . $code;
    $email_subject = 'Your unique customer code!';
```
and make language defines for them:
```php
  define('EMAIL_SUBJECT_EXTRA_EMAIL_WELCOME', 'Your unique customer code!');
  define('EMAIL_TEXT_EXTRA_EMAIL_MESSAGE', 'Here is your unique code: ');
```
and change the code to use those constants in place of the text.
```php
    $email_text = EMAIL_TEXT_EXTRA_EMAIL_MESSAGE . $code;
    $email_subject = EMAIL_SUBJECT_EXTRA_EMAIL_WELCOME;
```
Now those define statements can be placed into new files in corresponding language folders so they can be 
translated to suit whatever language the customer has selected while visiting the site. 
The define statements would go into a file at 
`/includes/languages/NAME_OF_A_LANGUAGE_HERE/extra_definitions/send_extra_email_at_welcome.php`.

**(REALLY those language defines, and the file, should be constructed according to updates methods added since v1.5.8. See the Docs for language files, for details)**


_This article inspired by a [community discussion](https://www.zen-cart.com/showthread.php/199729-How-to-assign-unique-account-numbers-OR-usernames?p=1148601#post1148601) for a more specific use-case._

