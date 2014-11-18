<!-- Security -->
# No Debug

PHP has a number of convenient functions for understanding the environnement in which it is executed or display inner information. This should be replaced by modern debuggers, that will provide a more convenient to assess a situation, and will not leave any unwanted instructions in the code.

```php
<?php

var_dump($variable);
print_r($tmp);

?>
```

## Rule Details

This rule apply to the following functions, when in production : 
* [var_dump](http://php.net/manual/en/function.var-dump.php)
* [print_r](http://php.net/manual/en/function.print-r.php)
* [debug_backtrace](http://php.net/manual/en/function.debug-backtrace.php)
* [debug_print_ backtrace](http://php.net/manual/en/function.debug-print-backtrace.php)
* [debug_zval_dump](http://php.net/manual/en/function.debug-zval-dump.php)
* [Magic method __debugInfo()](http://php.net/manual/en/language.oop5.magic.php#language.oop5.magic.debuginfo)

The following code is considered a warning:

```php
<?php

var_dump($variable);
print_r($tmp);

print_r(debug_backtrace());

?>
```

Rule may also apply to libraries build on top of `var_dump` concept, such as [Kint](http://raveren.github.io/kint/) or [Krumo](http://krumo.sourceforge.net/). They provide configuration to disable them while leaving debug traces in the code, which is not the case for native PHP functions such as `print_r`. While this is indeed better, this still mean code that won't be used is pushed to production. As such, it must be avoided. 

<!--
## When Not To Use It
Please, always use this

## Further Reading

-->