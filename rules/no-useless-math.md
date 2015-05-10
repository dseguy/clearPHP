<!-- Good Practices -->
# No Useless Math

Adding 0 to a number or multiplying it by 1 leaves the processed value unchanged : those are identity functions, in maths term. On the other hand, this is waste in PHP, as it will force the processing of a value that will eventually be the same. 

In PHP, `* 1` and `+ 0` have the side effect of type casting the value to integers or real numbers. Then, why not use the efficient casting operator `(int)`, which will also makes the intention clearer? 

```php
<?php

$a = "10";
$a += 0; // $a now is 10 (the integer), not 10 (the string)

?>
```

It is recommended to remove identity math operations, or to change them explicitly to a typecast.

## Rule Details

The following patterns are considered warnings:

```php
<?php

// Definitions
$a = "10";
$a = +0;
$a = -0;
$a = +100; // whatever the value
$a = +100.0; // whatever the value

$a = 0.0;

// Additions
$a = "10";
$a += 0;
$a -= 0;

// Multiplication
$a *= 1;
$a /= 1;
$a % = 1;
$a = $a + 1;
$a = $b / 1;
$a = $c % 1;

// also applies to power
$a **= 1;
$a = 1 ** $b;
$a = 0 ** $b;

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

