<!-- Good Practices -->
# Always Typehint

PHP allows the use of `<classname>`, `array` or `callable`, to type the incoming arguments as, respectively, objects of the class `<classname>`, arrays or callable functions. 

Whenever possible, typehint should be used so as to give more information about the incoming values. This will be used by PHP compiler and binary to check variables and, eventually, emits catchable exceptions when they are not. 

It is recommended to always set the typehint.

## Rule Details

This rule is aimed at encouraging the use of typehint.

The following patterns are considered warnings:

```php
<?php

function foo($a) {
	// $a should be typehinted with some class that support `callMethod` method.
	$a->callMethod();
}
?>
```

The following patterns are not considered ambiguous:

```php
<?php

function foo($a) {
	$b = $a . 1; // $a could be a string or an object that suport __toString()
}

?>
```

The following patterns are not considered warnings:

```php
<?php

function foo($a) {
	$b = $a + 1; // $a should be an integer
	$c = $a + 1.2; // $a should be an real
}

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

