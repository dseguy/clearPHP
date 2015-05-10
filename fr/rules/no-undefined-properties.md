<!-- Good Practices -->
# No Undefined Properties

Within a class, properties must be defined explicitly, using `private`, `protected` or `public`, in the class itself or in one of its parent. 

Undefined properties are accepted if the magic property methods are set for the class or its parent. 

```php
<?php

class foo {
	function doSomething() {
		$this->undefinedProperty = 1;
	}
}

?>
```

It is recommended to always declare properties. It makes the code clearer to read, and provides an opportunity to add documentation. 

## Rule Details

The following patterns are considered warnings:

```php
<?php

class foo {
	function doSomething() {
		$this->undefinedProperty = 1;
		
		self::undefinedStaticClass = 2;
	}
}

?>
```

The following patterns are not considered warnings:

```php
<?php

class bar {
	protected $barProperty = 1;
}

trait aTrait {
	protected $aTraitProperty = 1;
}

class foo extends bar {
	use aTrait;
	
	protected $fooProperty = 2;
	private static $fooStaticProperty = 3;
	
	function doSomething() {
		$this->barProperty++;
		$this->fooProperty++;
		$this->aTraitProperty ++;
		
		self::fooStaticProperty = 2;
	}
}

class foo2 {
	private $internals = array();
	
	function doSomething() {
		$this->undefinedProperty = 2;
	}
	
	public function __get($name) {
		return $this->internals[$name];
	}

	public function __set($name, $value) {
		$this->internals[$name] = $value;
	}
}


?>
```

<!--
### Options

## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically. 

## Further Readings
-->

