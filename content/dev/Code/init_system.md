---
title: Init System
category: code
weight: 10
---

The term initSystem, apart from being a tag used to group certain PHP files together in the new documentation, is meant to embrace all of those files that are automatically included/initialised before any 'command' scripts can be run.

Zen Cart v1.x uses a (non Object Oriented) page controller pattern to decide the scripts to run, based on HTTP`GET parameters. The most important of these is the 'main`page' HTTP`GET parameter. Depending on that parameter, a command script is then run. Each commmand script resides in a directory in `/includes/modules/pages`.

For example if `main`page=login` the command script would be taken from the `/includes/modules/pages/`login`/` directory. However the first thing every command script always does is require() the `/includes/application_top.php` file. This is the heart of the initSystem.

It is `application_top.php` that is responsible for initialising basic subsystems (database abstraction/sessions/languages etc.) and loading global configuration data. In the past this was done using a hard-coded script. From v1.3.0 on, however, Zen Cart now uses a control array to decide which functions/classes/data files are to be included and initialised. This allows contribution authors and third party developers to gain access to and extend the initSystem without compromising upgradeability.

In the following sections we will work through exactly how the Zen Cart engine uses `application_top.php` to initialise core systems.

### <span class="mw-headline" id="application_top.php`-`A`little`bit`of`history">application_top.php - A little bit of history</span>

In terms of its osCommerce roots, `application_top.php` was the file included on every page/script needed to invoke and handle basic core sub-systems. Any function/class that was needed globally by any page needed to be initialised here.

From a customisation perspective this was a bad thing. If third party code (contributions) needed to access a new global function/class then `application_top.php` would need to be 'hacked'. This would obviously cause problems on upgrades, when `application_top.php` would be overwritten, and any customisations would be lost.

Zen Cart attempted to mitigate this by providing certain override directories where extra data/functions files could be placed that would be automatically included when `application_top.php` was run.

The problem with this system is that it only provides for a very few places within the running order of `application_top.php` where new code can be introduced. It also did not provide at all for the addition of new classes. What was required was an `application_top.php` that allowed for the placing of any new function/class/script that was completely under the developer's control. Futhermore, some method of loading and invoking classes was also required.

Since v1.3, Zen Cart achieves this by abstracting the code run by `application_top.php` into a control array. This array stores details of functions/classes/init scripts that need to be run, and the order in which they are run in a special PHP array. Given this it is now possible for third party developers to 'hook' into `application_top.php` and be confident that any future code upgrades will not normally overwrite their own code.

### <span class="mw-headline" id="application_top.php`-`Breakpoints">application_top.php - Breakpoints</span>

In Zen Cart there is now almost no procedural code in `application_top.php`. The small amount that is there will be discussed later. The bulk of procedural code in `application_top.php` is now given over to handling breakpoints. Breakpoints can simply be described as points of importance. We currently have approximately 20 breakpoints in `application_top.php`. At each breakpoint something important happens - we may load a function or class, initialise a class, load a script fragment, and so on. The important point is to recognise that at each breakpoint, third party code can, by adding to the control array, also load functions, load classes, initialise classes, run a class method or load (require) a script fragment.

### <span class="mw-headline" id="The`Control`Array">The Control Array</span>

Control arrays are automatically loaded from the directory /includes/auto`loaders. Every `*.php` file within that directory is expected to have a certain structure. In v1.3 we use a file called `config.core.php` as the main file for governing `application_top.php`. Third party developers can add their own control array files. The structure of each file should look like this:

<pre> $autoLoadConfig[0] = array(`);` 
</pre>

The value after $autoLoadConfig (in this case [0]) represents the order in which the actions happen (e.g. the Breakpoint), such that $autoLoadConfig[0] will occur before $autoLoadConfig[1]. Note also that any two entries where the breakpoint is the same will occur in the order they appear within the file. The actual contents of the array(`) part depends upon what effect is needed. Let's consider a number of different scenarios.`

First I just want to require a file to be loaded. For this, the control array entry would be:

<pre> $autoLoadConfig[0][] = array('autoType'=>'require', 'loadFile'=> DIR`WS`INCLUDES . 'somefile.php'); 
</pre>

The `autotype` parameter tells us that we just want to require a file

The `loadFile` parameter tells us which file we want to load.

Loading function files can also obviously be done using the above.

Similarly if we want to 'include' a file:

<pre> $autoLoadConfig[0][] = array('autoType'=>'include', 'loadFile'=> DIR`WS`INCLUDES . 'somefile.php'); 
</pre>

We then have a special type of 'require'. The initSystem introduces a special class of `.php` files called init` scripts. These are stored in the includes/init`includes directory. Each of these contains a small amount of procedural code that can be run as part of the initSystem process. The reason for separating them out into a special directory is to allow for those init`scripts to be overridden, more of which will be discussed later. For now, to load an init`script we use the following control array structure.

<pre> $autoLoadConfig[] = array(array('autoType'=>'init`script', 'loadFile'=> 'init`database.php'));
</pre>

Where the auto`loader system comes into its own is in the handling of class files. With a class file we want to load the class file definition, then instantiate the class, and finally possibly run a class method (all running thus within the scope of `application_top.php`)

In terms of the control array we have the following entries to help us.

<pre> $autoLoadConfig[0][] = array('autoType'=>'class',
                               'loadFile'=>'shopping`cart.php');
</pre>

<pre> $autoLoadConfig[30][] = array('autoType'=>'classInstantiate',
                               'className'=>'cache',
                               'objectName'=>'zc`cache');
</pre>

<pre> $autoLoadConfig[80][] = array('autoType'=>'classInstantiate',
                               'className'=>'shoppingCart',
                               'objectName'=>'cart',
                               'checkInstantiated'=>true,
                               'classSession'=>true);
</pre>

<pre> $autoLoadConfig[120][] = array('autoType'=>'objectMethod',
                               'objectName'=>'navigation',
                               'methodName' => 'add`current`page');
</pre>

Taking these options one by one

Where autotype=>'class' all we are really doing here is 'including' the 'loadFile'. However, in this case we draw the file from the includes/classes (DIR`WS`CLASS) directory.

Where autotype=>'classInstantiate' executes code of the form objectName = new className();

An example based on the code above is

<pre> $zc`cache = new cache();
</pre>

One corollary to this is that we may need to instantiate a class that is bound to a session, like the shopping`cart class. In this case as from the example above we get

<pre> $_SESSION['cart'] = new shoppingCart();
</pre>

and in fact we take that one step further, Normally we only want to instantiate a session object if it is not already a session object. In this case we take advantage of the 'checkInstantiated' property, which would generate code:

<pre> if (!$_SESSION['cart']) {
   $_SESSION['cart'] = new shoppingCart();  
 }  
</pre>

The final example, where autotype-'objectMethod' shows how to run a class method within `application_top.php`. `At the time of writing there is no provision for passing method parameters`, so the code generated would be (based on the example above):

<pre>  $navigation->add`current`page();
</pre>

#### <span class="mw-headline" id="Notes`on`admin`autoloaders">Notes on admin autoloaders</span>

The goal of v1.3.x is to eventually remove and refactor all functions into classes. Further, these classes will be common between admin and catalog code.

However this presents a problem with the autoloading of class files. Currently the autoloader code, will default to loading a class from the catalog includes/classes directory rather than admin/includes/classes.

To provide for that interim period where we still need to to load admin class files from admin/includes/classes, we provide an extra option to the 'autotype'=>class option.

consider this

<pre> $autoLoadConfig[0][] = array('autoType'=>'class',
                              'loadFile'=>'class.base.php');
</pre>

if this is used in an admin autoloader it will load the class from the catalog classes directory. For the base class this is fine as the code can be shared between catalog and admin. However, at the moment the split`page`results`class is different between admin and catalog. So in order to load an admin-specific class we use:

<pre> $autoLoadConfig[0][] = array('autoType'=>'class',
                              'loadFile'=>'split`page`results.php',
                              'classPath'=>DIR`WS`CLASSES);
</pre>

### <span class="mw-headline" id="Overriding.2FExtending`the`system`autoloader">Overriding/Extending the system autoloader</span>

There are two ways of overriding/extending the inbuilt auto`loader and thus affecting what happens during the loading of `application_top.php`.

The usual method would be to simply add a new file to the `/includes/auto`loader/` directory. The file you add here should have start with `config` and have a `.php` extension (ie: `config.your`app`name.php`), and should contain one or more control array definitions. `This is the recommended method` to use for adding code to be executed within `application_top.php`, and allows contribution authors to customise the code here in a way that will be generally unaffected by system upgrades.

Additionally, within the `/includes/auto`loader/` directory is another directory called `overrides`. This can be used to override any autoloader file in the `/includes/auto`loader/` directory. For example, the main autoloader file used in Zen Cart is `config.core.php`. If a file called `config.core.php` is placed in the overrides directory, this will be used instead of the original.

### <span class="mw-headline" id="init`scripts`and`application_top.php">init`scripts and application_top.php</span>

#### <span class="mw-headline" id="Introduction">Introduction</span>

The initSystem allows you to automate the including/requiring of files and to automate the loading/instantiating of classes. However we still also need to be able to run some procedural code. We also want to allow 3rd parties to override that procedural code. init`scripts allow us to do this.

#### <span class="mw-headline" id="init`scripts">init`scripts</span>

There are currently 18 init`scripts in the base 1.3.0 release. These init`scripts are in the `includes/init`includes` directory.

*   init`add`crumbs.php (Responsible for initialising the Breadcrumb)
*   init`cart`handler.php (Responsible for handling Cart actions)
*   init`category`path.php (Reponsible for initialising Category Paths)
*   init`currencies.php (Responsible for initialising the Currencies Sub-System)
*   init`customer`auth.php (Responsible for checking customer status, either thru Down for Maintenance or the Approval level)
*   init`database.php (Responsible for initialising the DB layer)
*   init`db`config`read.php (Responsible for reading configuration data from database)
*   init`file`db`names.php (Responsible for loading File and Database tablename Defines)
*   init`general`funcs.php (Resposible for loading general functions from the includes/functions directory as well as the extra`functions folder)
*   init`gzip.php (Responsible for loading Gzip output-buffering functions)
*   init`header.php (Responsible for running page-header procedures)
*   init`languages.php (Responsible for loading multiple-language support sub-system)
*   init`sanitize.php (Responsible for loading input-sanitising code)
*   init`sefu.php (Responsible for loading code to provide search-engine-friendly URLs)
*   init`sessions.php (Responsible for loading Session code)
*   init`special`funcs.php (Responsible for loading specialized but necessary functions)
*   init`templates.php (Responsible for initialising the template System and activating template-specific language-content defines)
*   init`tlds.php (Responsible for setting Top Level Domain Variables)

#### <span class="mw-headline" id="Overriding`init`scripts">Overriding init`scripts</span>

It is very simple to override a core init script. The directory includes/init`incudes contains a directory called overrides. If I wanted to override the incudes/init`includes/init`sessions.php script then I would simply create a file called init`sessions.php in the includes/init`includes/overrides directory.

### <span class="mw-headline" id="Procedural`code`in`application_top.php">Procedural code in application_top.php</span>

Despite the use of the autoloader system, there is still a little procedural code left in application_top.php; although most of this procedural code is given over to processing autoloaders themselves.

Below is the code from the catalog `includes/application_top.php`. Note: I have removed all documentation tags for clarity

<pre>define('DEBUG`AUTOLOAD', false);
define('IS`ADMIN`FLAG', false);
define('PAGE`PARSE`START`TIME', microtime());
@ini`set("arg`separator.output","&");
if (file`exists('includes/local/configure.php')) {
  include('includes/local/configure.php');
}
if (defined('STRICT`ERROR`REPORTING') && STRICT`ERROR`REPORTING == true) {
  error`reporting(E`ALL);
} else {
  error`reporting(E`ALL & ~E`NOTICE);
}
if (file`exists('includes/configure.php')) {
  include('includes/configure.php');
} else {
  header('location: zc`install/index.php');
}
if (!is`dir(DIR`FS`CATALOG.'/includes/classes'))  header('location: zc`install/index.php');
if ($za`dir = @dir(DIR`WS`INCLUDES . 'extra`configures')) {
  while ($zv`file = $za`dir->read()) {
    if (preg`match('/\.php$/', $zv`file) > 0) {
      include(DIR`WS`INCLUDES . 'extra`configures/' . $zv`file);
    }
  }
} 
$loader`file = 'config.core.php';
$base`dir = DIR`WS`INCLUDES . 'auto`loaders/';
if (file`exists(DIR`WS`INCLUDES . 'auto`loaders/overrides/' . $loader`file)) {
  $base`dir = DIR`WS`INCLUDES . 'auto`loaders/overrides/';
}
include($base`dir . $loader`file);
if ($loader`dir = dir(DIR`WS`INCLUDES . 'auto`loaders')) {
  while ($loader`file = $loader`dir->read()) {
    if ((preg`match('/^config\./', $loader`file) > 0) && (preg`match('/\.php$/', $loader`file) > 0)) {
      if ($loader`file != 'config.core.php') {
        $base`dir = DIR`WS`INCLUDES . 'auto`loaders/';
        if (file`exists(DIR`WS`INCLUDES . 'auto`loaders/overrides/' . $loader`file)) {
          $base`dir = DIR`WS`INCLUDES . 'auto`loaders/overrides/';
        }
        include($base`dir . $loader`file);
      }
    }
  }
}
if (( (!file`exists('includes/configure.php') && !file`exists('includes/local/configure.php')) ) || (DB`TYPE == `) ||    (!file`exists('includes/classes/db/' .DB`TYPE . '/query`factory.php'))) {`
  header('location: zc`install/index.php');
  exit;
}
require('includes/autoload`func.php');
require(DIR`WS`INCLUDES . 'counter.php');
$customers`ip`address = $`SERVER['REMOTE`ADDR'];
if (!isset($_SESSION['customers`ip`address'])) {
  $_SESSION['customers`ip`address'] = $customers`ip`address;
}
</pre>
