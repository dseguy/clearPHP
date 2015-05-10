<!-- PHP Manual -->
# No Constant As Array Keys

PHP has a fallback to string when a constant is not defined. For example : 

```php
<?php

// foo is not defined as constant 

$a = array('foo' => 'bar');

// foo is a string, because of the quotes (double will do too)
echo $a['foo'];

// foo is a string, because it is inside double quotes
echo "$a[foo]";

// That won't compile
//echo "$a['foo']";

// That will be 'foo' (the string), or, the foo constant (when someone defines it)
echo $a[foo];

?>
```
It is recommended to always have index as strings or integers, so as to be consistent inside and outside quotes. Check weel that any constant used there is actually defined. Other types are cast or emit an error anyway.

## Rule Details

The following patterns are considered warnings:

```php
<?php

$a = array(1.0 => 'b',  // Float will be casted
		   '1' => 'c',  // String will be casted to Int when possible
		   true => 'd', // Boolean will be casted to Int
		   null => 'e', // Null will be casted to Empty string
	  	   foo  => 'f'  // const may be cast to its value or to String
			 );
 
?>
```

The following patterns are not considered warnings:

```php
<?php

const F = 10;
define('G' ,11);

$a = array(1 =>  'c', 
				    'd', // automated index
		 		    'a' => 'e',
		 		    F => 1, // F is defined
		 		    G => 2  // G is defined
			 );
 
?>
```

<!--
### Options

## When Not To Use It
-->

## Further Readings
*[Arrays](http://php.net/manual/en/language.types.array.php)

