<!-- Good Practices -->
# No Unthrown Exceptions

PHP supports exceptions. Exceptions are defined by extending the `\Exception` class and then thrown when an error needs to be reported. 

```php
<?php

class unusedException extends \Exception {}

class divisionByZero extends \Exception {}

$a = 1;
$b = 0;

if ($b === 0) {
	throw new divisionByZero();
}

print $a / $b."\n";

?>
```
It is recommended to remove any exception that is not thrown at least once in the rest of the application.

<!--
### Options

## When Not To Use It

## Further Readings
*[Arrays](http://php.net/manual/en/language.types.array.php)

-->