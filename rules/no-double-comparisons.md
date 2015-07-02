<!-- Good Practices -->
# No Double Comparisons

Floating point numbers is the type of value that represents decimal numbers in PHP. They may also be called `double`, `float` or `real`. 

```php
<?php
	$double = 1.234;
	var_dump($double);
	// double(1.234);
	
	// from the manual 
	$b = 1.2e3;   // including 
	$c = 7E-10;
	
?>
```

As stated in the manual : "testing floating point values for equality is problematic, due to the way that they are represented internally. ". Direct comparisons should always be avoided, as some random rounding error may happen, and it will make the most simple comparison fails.

```php
<?php
$a = 85 - 2.4;  // which is equal to 2.6
$b = 2.6;
var_dump($a == $b); // is not true
?>
```

Comparisons involving double must be done using an error margin, like this : 

```php
<?php
$a = 85 - 2.4;  // which is equal to 2.6
$b = 2.6;

var_dump(abs($a-$b) < 0.00001); // This is true
?>
```

In this example, the error margin is `0.00001`. 

It is recommended to avoid comparing literal float or expression using float directly, with the equality operators. When possible, float may be avoided alltogether, and replaced with integers or one of the PHP extensions that deals with arbitrary precision mathematics. 

## Rule Details

The following pattern is considered warnings:

```php
<?php

if ($a == 1.2) {}

if (3.4 != $b) {}

if (5.6 + $c !== $b) {}

?>
```

The following pattern are considered legit:

```php
<?php

// Use an application constant to make all operations consistant
const FLOAT_PRECISION = 0.000001;

if (abs($a - 1.2) < FLOAT_PRECISION ) {}

// Above requested precision means 'different'
if (abs(3.4 - $b) > FLOAT_PRECISION) {}

if (abs(5.6 + $c - $b) > FLOAT_PRECISION ) {} 

?>
```
<!--
### Options
## When Not To Use It

If needed, just use revert from the control version system. 
-->

## Further Reading 
* [Floats](http://php.net/float)
* [BC Maths](http://php.net/bc)
* [GMP](http://php.net/gmp)

