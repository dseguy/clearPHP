<!-- PHP Manual -->
# Default Argument At The End

When defining a method, it is possible to provide a default value to arguments : there only need to add the value after the argument's name and the equal sign.

```php
<?php

function withoutDefault($a) {} 
function withDefault($a = 1) {} 

?>
```

In the above example, the function `withDefault` has one argument, with a default value of `1`. Now this argument may be omitted at calltime, and it will be available in the function with a value of one. PHP makes use of such arguments for functions such as `htmlentities` or `array_unique`. 

PHP only accepts arguments with default values when they are the last of the arguments. Like this : 

```php
<?php

function withDefault($a, $b, $c = 1, $d = 2 ) {}
function withDefault2($a, $b, $c = 1, $d = 2, $e = 'd' ) {}

?>
```

Both functions have, respectively, two and three arguments and two compulsory arguments. This way, when they are called with only 2 arguments, the last ones will be filled with default values.

The catch here is that PHP doesn't enforce the instructions from the manual. It is possible to declare any argument with a default value, and have the code compile correctly. The catch will come at execution time 

```php
<?php

function f($a, $b = 1, $c ) {
	echo $a, $b, $c, "\n";
}

f(1,2,3); // display 123
f(1,3);   // display 13 and an error

?>
```

PHP will still assign the incoming arguments in the calling order. When he runs out of values, it will try to find a default value in the definition, but without it, it concludes that the argument is missing. 

It is important to check that only the last arguments have default values. 

## Rule Details

This rule applies the instructions from the PHP manual, and no the PHP binary behavior.

The following patterns are considered warnings:

```php
<?php

function f($a = 1, $b) {}

function f($a = 1, $b, $c = 3) {}

function f($a = 1, $b, $c = 3, $d) {}

?>
```

The following patterns are not considered warnings:

```php
<?php

function f($a = 1, $b = 2) {}

function f($a = 1, $b = 2, $c = 3) {}

function f($a, $b, $c, $d) {}

?>
```

<!--
### Options
-->

## When Not To Use It
Always use it. 

## Further Readings
* [Function arguments](http://php.net/functions.arguments) (See Example #5 Incorrect usage of default function arguments)
