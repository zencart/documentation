---
title: Init System
description: How Zen Cart bootstraps itself 
category: code
weight: 10
---

The initSystem refers to all of those files that are automatically included/initialised before any `command` scripts can be run.

Zen Cart v1.x uses a (non Object Oriented) page controller pattern to decide the scripts to run, based on `HTTP_GET` parameters. The most important of these is the `main_page` parameter. Depending on that parameter, a command script is then run. Each commmand script resides in a directory in `/includes/modules/pages`.

For example if `main_page=login` the command script would be taken from the `/includes/modules/pages/login/` directory. 

However the first thing every command script always does is `require()` the `/includes/application_top.php` file. This is the heart of the initSystem.

It is `application_top.php` that is responsible for initialising basic subsystems (database abstraction/sessions/languages etc.) and loading global configuration data. 

Zen Cart uses a control array to decide which functions/classes/data files are to be included and initialised. This allows contribution authors and third party developers to gain access to and extend the initSystem without compromising upgradeability.

The following sections describe how the Zen Cart engine uses `application_top.php` to bootstrap itself and initialise core systems.

### application_top.php - Breakpoints

The focus of `application_top.php` is primarily to set up some core requirements, and then process the auto_loader breakpoints as described below.

Breakpoints can simply be described as points of importance. 

At each breakpoint something important happens: we may load a function or class, initialise a class, load a script fragment, and so on. 
The important point is to recognise that at each breakpoint, third party code can, by adding to the control array, also load functions, load classes, initialise classes, run a class method or load (require) a script fragment.

### The Control Array

Control arrays are automatically loaded from the directory `/includes/auto_loaders`. 
Every `*.php` file within that directory is expected to have a certain structure. 

The master `config.core.php` is the main file for governing `application_top.php`, and should not be altered. 

Third party developers can add their own control array files. 

The structure of each file should look like this:

<pre> 
$autoLoadConfig[0] = array(); 
</pre>

The value after $autoLoadConfig (in this case `[0]`) represents the order in which the actions happen (e.g. the Breakpoint), such that `$autoLoadConfig[0]` will occur before `$autoLoadConfig[1]`. 

Note also that any two entries where the breakpoint is the same will occur in the order they appear within the file. 

The actual contents of the `array()` part depends upon what effect is needed. 

Let's consider a number of different scenarios.

#### require
First the case of just wanting to `require` a file to be loaded. For this, the control array entry would be:

```
$autoLoadConfig[0][] = array('autoType'=>'require', 'loadFile'=> DIR_WS_INCLUDES . 'somefile.php'); 
```

The `autotype` parameter tells us that we just want to `require` a file

The `loadFile` parameter tells us which file we want to load.

Loading `function` files can also obviously be done using the above. (Alternatively they could just be placed in the `extra_functions` directory.)


#### include
Similarly if we want to `include` a file:

```
$autoLoadConfig[0][] = array('autoType'=>'include', 'loadFile'=> DIR_WS_INCLUDES . 'somefile.php'); 
```

#### init scripts
The initSystem introduces a special class of `.php` files called **init scripts**. 

These are stored in the `includes/init_includes` directory. 

Each of these contains a small amount of procedural code that can be run as part of the initSystem process. 

The reason for separating them out into a special directory is to allow for those init_scripts to be overridden, more of which will be discussed later. 

To load an `init_script` we use the following control array structure:

<pre>
$autoLoadConfig[] = array('autoType'=>'init_script', 'loadFile'=>'init_database.php');
</pre>

#### classes
Classes often require special handling. With a class file we want to load the class file definition, then instantiate the class, and finally possibly run a class method (all running thus within the scope of `application_top.php`)

In terms of the control array we have the following entries to help us.

<pre>
  $autoLoadConfig[0][] = array('autoType'=>'class',
                               'loadFile'=>'shopping_cart.php',
                               );
</pre>

<pre>
 $autoLoadConfig[30][] = array('autoType'=>'classInstantiate',
                               'className'=>'cache',
                               'objectName'=>'zc_cache',
                               );
</pre>

<pre>
 $autoLoadConfig[80][] = array('autoType'=>'classInstantiate',
                               'className'=>'shoppingCart',
                               'objectName'=>'cart',
                               'checkInstantiated'=>true,
                               'classSession'=>true,
                               );
</pre>

<pre>
 $autoLoadConfig[120][] = array('autoType'=>'objectMethod',
                                'objectName'=>'navigation',
                                'methodName' => 'add_current_page',
                                );
</pre>

Taking these options one by one

#### class
Where `autotype=>'class'` all we are really doing here is 'including' the 'loadFile'. However, in this case we draw the file from the includes/classes (DIR_WS_CLASS) directory.

#### classInstantiate
If `autotype=>'classInstantiate'` is specified it instantiates the class as: `objectName = new className();`

An example based on the code above is

<pre>
$zc_cache = new cache();
</pre>

#### objectName
One corollary to this is that we may need to instantiate a class that is bound to a session, like the shopping_cart class. 
In this case as from the example above we get

```
$_SESSION['cart'] = new shoppingCart();
```

and in fact we take that one step further:

#### checkInstantiated
Normally we only want to instantiate a session object if it is not already a session object. 
In this case we take advantage of the `checkInstantiated` property, which would generate code:

```
if (!$_SESSION['cart']) {
   $_SESSION['cart'] = new shoppingCart();  
 }  
```

#### objectMethod
To call a class method in the scope of `application_top.php`, use `autotype='objectMethod'`

The code generated would be (based on the example above):

```
$navigation->add_current_page();
```

#### classPath
Unless otherwise specified, the path where a class file is expected to be found is the catalog classes directory.
To override that you can pass a `classPath` of `DIR_WS_CLASSES` or a specific directory path.

For example:

<pre>
 $autoLoadConfig[0][] = array('autoType'=>'class',
                              'loadFile'=>'split_page_results.php',
                              'classPath'=>DIR_WS_CLASSES);
</pre>

### Extending the system autoloader
To add additional loading/instantiation actions, add a new file to the `/includes/auto_loader/` directory. 

The file you add here should have start with `config` and have a `.php` extension (ie: `config.yourapp_name.php`), and should contain one or more control array definitions. 

**This is the recommended method** to use for adding code to be executed within `application_top.php`, and allows contribution authors to customise the code here in a way that will be generally unaffected by system upgrades.


### init_scripts

The `init_scripts` allow us to run some procedural core code.

And also allows 3rd party plugins to override that procedural code. 


#### core init_scripts

There are several default init_scripts in core code, located in the `includes/init_includes` directory. Similar files exist also in the Admin directory structure.

```
*   init_add_crumbs.php (Responsible for initialising the Breadcrumb)
*   init_cart_handler.php (Responsible for handling Cart actions)
*   init_category_path.php (Responsible for initialising Category Paths)
*   init_currencies.php (Responsible for initialising the Currencies Sub-System)
*   init_customer_auth.php (Responsible for checking customer status, either thru Down for Maintenance or the Approval level)
*   init_database.php (Responsible for initialising the DB layer)
*   init_db_config_read.php (Responsible for reading configuration data from database)
*   init_file_db_names.php (Responsible for loading File and Database tablename Defines)
*   init_general_funcs.php (Responsible for loading general functions from the includes/functions directory as well as the extra_functions folder)
*   init_gzip.php (Responsible for loading Gzip output-buffering functions)
*   init_header.php (Responsible for running page-header procedures)
*   init_languages.php (Responsible for loading multiple-language support sub-system)
*   init_sanitize.php (Responsible for loading input-sanitising code)
*   init_sefu.php (Responsible for loading code to provide search-engine-friendly URLs)
*   init_sessions.php (Responsible for loading Session code)
*   init_special_funcs.php (Responsible for loading specialized but necessary functions)
*   init_templates.php (Responsible for initialising the template System and activating template-specific language-content defines)
*   init_tlds.php (Responsible for setting Top Level Domain Variables)
```

#### Overriding init_scripts

It is very simple to override a core init_script. The directory `includes/init_includes` contains a directory called `overrides`. 

If I wanted to override the `includes/init_includes/init_sessions.php` script then I would simply create a file called `init_sessions.php` in the `includes/init_includes/overrides` directory.

