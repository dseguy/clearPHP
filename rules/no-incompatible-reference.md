<!-- PHP Manual -->
# No Incompatible References

When calling a method or a function, the arguments passed by reference, and signaled in the signature by `&`, must be one of the following : 
* Variables or arrays : `$v` or `$x[1]`
* New objects : `new stdClass()`
* References

```php
<?php

parse_str($incomingString, 'string');
?>
```

PHP only check that functioncall are using valid type at execution time, if the definition of the method is not available at compile time (aka, the method is not native or not defined in the same file than call). 

```php
<?php

// definition file, to be included in the next code
function foo(&$string) { /**/ }

?>
```


```php
<?php

foo('PHP'); // This will yield a Fatal error at execution

?>
```

It is recommended to ensure that passed-by-reference argument are of the requested type. 

## Rule Details

The following patterns are considered warnings:

```php
<?php

function foo(&$string) { /**/ }

foo('PHP'); // String
foo(true);  // Boolean
foo(1);  // Integer
foo(1.2);  // Float
foo(null);  // NULL
foo(PHP_VERSION);  // Constant
foo(SomeCLass::Constant);  // Static constant

?>
```
The following patterns are not considered warnings:

```php
<?php

function foo(&$string) { /**/ }

foo($variable); // Variable
foo($array[1]); // Array
foo($object->property);  // Property
foo(SomeClass::$property);  // Static Property
foo(ReferenceReturningFunction());  // Reference Returning Function
foo($object->ReferenceReturningMethod());  // Reference Returning Function
foo(Classe::ReferenceReturningStaticMethod());  // Reference Returning Function

function &ReferenceReturningFunction() {
    $x = 1;
    return $x;
}


?>
```

<!--

### Options
-->
## When Not To Use It
Always use this.

## Further Readings
* [Passing references as arguments](http://php.net/manual/en/language.references.pass.php)
* [Functions arguments](http://php.net/manual/en/functions.arguments.php)
