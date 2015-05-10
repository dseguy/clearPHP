<!-- Good Practices -->
# No Closure Argument Collisions

When defining a closure, two kinds of variables may be including in the following code : 
* The one used as arguments
* The one stated in the `use` statement

```php
<?php

$a = 1;

$f = function ($b) use ($a) {
	return $a + $b;
};

?>
```

PHP will not check for any collision between arguments and imported variables : instead, it will overwrite the importer variable will have precedence over the argument. For example : 

```php
<?php

$a = 1;

$f = function ($a) use ($a) {
	return $a + $a;
};

print $f(2); // this will print '2', aka 1 + 1;

?>
```

It is recommended to make sure that all arguments and imported variables are distinct. 

## Rule Details

The following patterns are considered warnings:

```php
<?php

function ($a) use ($a) {
	return $a + $a;
};

function ($a, $b, $c) use ($a) {
	return $a + $a;
};

function ($a) use ($a, $b, $c) {
	return $a + $a;
};

?>
```

The following codes are not considered warnings:

```php
<?php

function ($a, $b, $c) use ($d, $e, $f) {
	return $a + $b + $c + $d + $e + $f;
};

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

