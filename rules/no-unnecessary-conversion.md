<!-- Performances -->
# No Unnecessary Conversion

PHP does a lot of type juggling : this means that it will automatically cast values from one type to the other, if the current operation requires it. 

```php
<?php

$a = "5";
$b = 1 + (int) $a;
$c = 'c' . (string) $a); // both unnecessary : $a is a string 
					     // and concatenation will require one anyway

?>
```

Typecasting will be useful as security feature, to ensure a value is of a requested type. It will not help performances. 

It is recommended to avoid recalculation in any function scope. In the global scope, this is also recommended, although it may be harder to spot. 

## Rule Details

This rule is aimed at avoiding useless typecasting.

The following patterns are considered warnings:

```php
<?php

$a = "5";
$b = 1 + (int) $a;
$c = 1.0 + (int) $a;

$d = 'd' . ((string) $a); 

// do not cast unknown fraction to integers
echo (int) ( (0.1+0.7) * 10 ); // echoes 7!
// uses floor() or ceil() instead

?>
```
<!--
The following patterns are not considered warnings:

```php
<?php


?>
```


### Options

## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically. 
-->

## Further Readings
* [Casting integers] (http://php.net/manual/en/language.types.integer.php#language.types.integer.casting)
* [floor] (http://php.net/floor)
* [ceil] (http://php.net/ceil)

