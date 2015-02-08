<!-- Good Practices -->
# No Raw Exception

PHP handles exceptions. `Exception` is the eponymous class, that is the mother of all exceptions : PHP's SPL exceptions, extensions Exceptions (mysqli, pdo, phar, soap, etc..) and, eventually, the one in the final application.

Thrown exceptions should inherit from `Exception`. This way, they may be selectively caught by a `try...catch` structure. 

```php
<?php

try {
	/* Some Code */
	throw new MyException('Message');

} catch (MyException $e) {
	// Catch all
}

?>
```
Exceptions may be grouped for catch with an extra level of inheritance : 

```php
<?php

class WeekException extends Exception {}
class MonthException extends Exception {}

class MondayException extends WeekException {}
class TuesdayException extends WeekException {}
/*...*/

class JanuaryException extends MonthException {}
/*...*/

try {
	/* on Monday */
	throw new MondayException('Message');

	/* on Tuesday */
	throw new TuesdayException('Message');

} catch (WeekException $e) {
	// Process weekdays exceptions
	// do not process month exceptions
}

?>
```

Exceptions may also be nested : by throwing a new exception that include the previous one, both messages will be carried to the next `try...catch`. 

```php
<?php

try {
	/* on Monday */
	throw new MondayException('Message');
	
} catch (WeekException $e) {
	// Process monday exceptions
	throw new JanuaryException('Week day exception caught in January', null, $e); 
}

?>
```

Last, there are already 13 exceptions predefined in SPL extension : 

* BadFunctionCallException
* BadMethodCallException
* DomainException
* InvalidArgumentException
* LengthException
* LogicException
* OutOfBoundsException
* OutOfRangeException
* OverflowException
* RangeException
* RuntimeException
* UnderflowException
* UnexpectedValueException

They provide some general semantics for Exceptions and may be used to help libraries understand each other's exception. 

As Exception should be specialized, catching a precise type of exception should be preferred over catching `Exception` : this last one is actually reserved for a catch-all feature. 

It is recommended to extends the Exception and never directly use this class. 

## Rule Details

The following code is considered a warning:

```php
<?php

try {
	/* Some Code */
	throw new Exception('Message');

} catch (Exception $e) {
	// Catch all
}

?>
```

The following pattern is considered legit:

```php
<?php

try {
	/* Some Code */
	throw new MyException('Message');

} catch (DomainException $e) {
	// Catch SPL-inheriting exception
} catch (MySpecialException $e) {
	// Catch only my special type of exception
}

class MyException extends \DomainException {}

class MySpecialException extends \Exception {}

?>
```

<!--
## When Not To Use It
Catching `Exception` is accepted when it is used for a catch-all feature. 
-->

## Further Reading 

* [PHP Exceptions](http://php.net/manual/en/language.exceptions.php)
* [SPL Exceptions](http://php.net/manual/en/spl.exceptions.php)
* [Exception Best Practices in PHP 5.3] (http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3)
