<!-- Performances -->
# No Debug Code

Debug code is be of several flavor : 
* `var_dump` and `print_r`
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

## Further Readings
-->

