<!-- Good Practices -->
# No Useless Return

Some of PHP magic methods makes no usage of the returned value. Such methods may simply finish without return, or use the empty `return` instruction.

```php
<?php

class x {
	function __construct() {
		// construct the object
		
		return true; // return value is ignored.
	}
	
	function __destruct() {
		if (!$this->resource) {
			return ; // returns void, as a short cut
		}
		
		$this->close($this->resource);
		// implicit return;
	}
}


?>
```
It is recommended to omit return in those methods, unless for short circuiting it.

## Rule Details

This rule is aimed at avoiding use of `return` in methods that doesn't need it. Here is the list : 

* __constructor
* __destructor
* __set
* __clone
* __unset

Also `__autoload`, methods used for autoloading and methods registered for shutdown, have no need to return anything. 

The following patterns are considered warnings:

```php
<?php

class exampleClass {
	function __construct() {
		// construct the object
		
		return true; // return value is ignored.
	}
}

?>
```

The following patterns are not considered warnings:

```php
<?php

class x {
	function __unset($name) {
		return ; // short circuit the method
	}
	
	function __set($name, $value) {
		return null; // short circuit the method
	}

	function __clone() {
		// implicit return (aka none)
	}
}
?>
```

<!--
### Options

## When Not To Use It

## Further Readings
*[]()

-->
