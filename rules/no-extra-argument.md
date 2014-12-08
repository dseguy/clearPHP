<!-- Good Practices -->
# No Extra Argument

PHP does not check at compile time that a function or method calls has too many arguments. One may call any function with any number of arguments, and the extra arguments will be dropped at execution time.  

This is true for PHP native functions too.

```php
<?php

function x($a, $b, $c = 2) { return $a + $b; }

x(1, 2, 3, 4, 5); // two arguments too many

?>
```

It is recommended to provide only the needed arguments when calling a method or a function.

## Rule Details

This rule spots functions and methods calls with arguments than needed. 

When the called method makes use of variable number of argument, using `func_get_args`, `func_get_arg` or `func_num_args`, or even the `...` operator, the numbero of acceptable argument is 

The following codes are considered a warning:

```php
<?php

function x($a, $b, $c = 2) { return $a + $b; }

function z($a, ...$b) { 	return array_sum($b) + $a; }

x(1, 2, 3, 4); // extra argument 4

?>
```

The following pattern are considered legit:

```php
<?php

function x($a, $b, $c = 2) { 	return $a + $b; }
function y($a, $b, $c = 2) { 	return array_sum(func_get_args()); }
function z($a, ...$b) { 	return array_sum($b) + $a; }

x('a', 'b', 'c', 'd'); 

y();

z(1, 2, 3, 4); 

?>
```


<!--
## When Not To Use It



## Further Reading 
-->
* [func_get_arg](http://php.net/manual/en/function.func-get-arg.php)
* [func_get_args] (http://php.net/manual/en/aliases.php)
* [func_num_args](http://php.net/manual/en/function.func-num-args.php)
* [Variable-length argument lists](http://php.net/manual/en/functions.arguments.php#functions.variable-arg-list)
