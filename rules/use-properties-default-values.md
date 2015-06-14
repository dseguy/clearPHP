<!-- PHP Manual -->
# Use Default Property Values

It is possible to declare default values for properties. 

```php
<?php

class Dog {
	public $name = 'Rex';
	private $tatoo;
	
	public function __construct($tatoo, $name = null) {
		$this->tatoo = $tatoo; // only initialized with incoming data
		if ($name === null) {
			$this->name = $name; 
		} else {
			$this->name = 'Rex'; // May be omitted, as it is already the default value for name
		}
	}
}
?>
```

Default values are easier to find when they are set a declaration time, instead than in the middle of the code. This also means less code written in the constructor. 

It is recommended to set default values to properties. 

## Rule Details

The following are considered warning : 
```php
<?php

class x {
	public $a; //
	public $b; //
	
	function __construct($c) {
		$this->a = 2;  // should be set in the declaration
		
		if ($c == true) {
			$this->b = $c;
		} else {
			$this->b = 'default value'; // should be set in the declaration
		}
	}
}

?>
```

The following are considered legit : 

```php
<?php

class x {
	public $d = 1; // d has a default value and is not set in constructor
	public $e; // e is set with a constructor argument
	public $f; // f is set with a constructor argument
	
	function __construct($c) {
		$this->e = $c;  // no special default value
		
		if ($c === 1) {
			$this->f = 'd'; 
		} elseif ($c === 2) {
			$this->f = 'e'; 
		} else {
			$this->f = $c;
		}
	}
}

?>
```

<!--
## When Not To Use It
Please, always use this rule.

## Further Reading
* []()
-->