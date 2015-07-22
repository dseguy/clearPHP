<!-- Performances -->
# No Debug Code

Debug code is be of several flavor : 

* `var_dump` and `print_r`
* `debug_print_backtrace` and `debug_backtrace` (the latter one has to be printed)
* `$php_errormsg` variable (also when printed)
* `ini_set` with `display_errors` and `html_errors` directives
* `print` or `echo` with information (i.e. `echo 'DEBUG';`. That includes HTML comments or `$debug` messages.
* Helper functions or classes, such as Kint, php-ref, dump_r, Krumo, dBug.

```php
<?php

if (!is_object($dbconnexion)) {
	debug($dbconnexion);
	die();
}
?>
```

The most suited tool for debugging is a PHP debugger, that will run the code and give a full view of the situation, call stack and variable values. PHP debuggers also allow step by step execution. They are usually integrated with the IDE.

It is recommended to remove all mention to those tools in production code, so as to avoid situations where they are really used (and are in production). 

## Rule Details

The following patterns are considered warnings:

```php
<?php

print 'debug';

require '/kint/Kint.class.php';
Kint::dump( $_SERVER );

?>
```
<!--

### Options

## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically. 
-->

## Further Readings

* [6 Debugging Tips Every PHP Coder Should Know](http://markonphp.com/6-debugging-tips-php-coders-should-know/)
* [Kint](http://raveren.github.io/kint/)
* [php-ref](https://github.com/digitalnature/php-ref)
* [dump_r](https://github.com/leeoniya/dump_r.php)
* [Krumo](http://krumo.sourceforge.net/)
* [dBug](https://github.com/ospinto/dBug)
* [Whoops](http://filp.github.io/whoops/)

