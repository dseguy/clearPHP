<!-- Performances -->
# Always Preprocess

Everything that may be prepared before compiling will be less work for PHP at later stage. This usually leads to building cache into the application, as most data are dynamical and not known at compile time.

However, there is a range of optimization that are rooted in coding laziness : 

```php
<?php

$seconds = 24 * 60 * 60;

$seconds = 86400;

?>
```

The first initialization is based on literals multiplications, and will waste a few cycles to actually start the script. 

It is recommended to always precalculate values and avoid literals operations in code.

If it helps to keep the equation, comments will be the solution.

## Rule Details

This rule is aimed at avoiding using PHP to build initial values.

The following patterns are considered warnings:

```php
<?php

define ('DAY_IN_SECONDS', 24 * 60 * 60);
// define('DAY_IN_SECONDS', 86400);

$x = [];
$x[] = 'a';
$x[] = 'b';
// $x = ['a', 'b'];

?>
```

The following patterns are not considered warnings:

```php
<?php

define('b', $dbResult->count());

$s = 'Today is year '.date('Y');

// this is constant scalar expression
const someConstant = class::constante + 1;

?>
```

<!--
### Options
-->
## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically. 

<!--
## Further Readings
-->

