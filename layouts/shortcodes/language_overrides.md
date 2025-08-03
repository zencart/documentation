When you want to override a language file, you don't 
have to reproduce the whole file and make your changes - you can include just
the changes you want.  An example is provided by the [Bootstrap](/user/template/bootstrap/) template, in
its override of the `includes/languages/lang.english.php` file. 

The file `includes/languages/bootstrap/lang.english.php` file (in version 3.7.7) looks like this:

```
$define = [
    'TEXT_MISSING_SHIPPING_INFO' => 'WARNING: missing shipping details',
];
return $define;
```

so instead of reproducing all 500 array elements and changing only one, 
this technique allows you to just include the one that has been changed.
