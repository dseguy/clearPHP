<!-- Good Practices -->
# Definitions Only Files

PHP allows the definitions of structures that will be later called by other part of the program : constants, functions, classes, interfaces and traits. 

```php
<?php

function x($a, $b) { 
	return $a + $b;
}
?>
```

Those definitions are inert : they won't run by themselves, without being called. 

On the other hand, global code, which isn't part of a previously mentioned structures, will be run directly and expect the called expressions be defined.

It is recommended to avoid mixing global code and definitions. This way, including definitions will not alter the execution of the program, beside adding new functionalities; And global code will only run code, and not add anything else.

Inclusion (with `require` and similar functions) are not acceptable for this rule : configuring (or including) the autoloader is global code, and should be loaded in another part of the script.

## Rule Details

This rule is aimed at avoiding mixing global code and definitions. 

This rule will tolerate that several structures are defined in the same file. The rule that requires only one structure per file is a distinct one. 

The following patterns are considered warnings:

```php
<?php

define ('DB_ACCESS',true);

$db = new DatabaseConnexion();

?>
```

Inclusions (such as the `require_once` below) are not acceptable 

```php
<?php

require_once __DIR__ . '/Autoloader.php';

trait T {
	/**/
}

?>
```

The following patterns are not considered warnings:

```php
<?php

define('b', $dbResult->count());

class DatabaseConnexion {
	/**/
}
?>
```

```php
<?php

namespace a;
use b;

global $c; 

trait DatabaseConnexion {
	/**/
}

?>
```

<!--
### Options
-->
<!--
## When Not To Use It
-->

## Further Readings
* [PSR-1 : Side effects](http://www.php-fig.org/psr/psr-1/)

