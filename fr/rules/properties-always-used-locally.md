<!-- Good Practices -->
# Properties Used Locally

At least, properties should be used in the class or trait where they are defined. 

Check the code below : `$name` is defined in a `Human` class, as a universal characteristics. However, the methods manipulating that property are located in the child class `Man`. 

```php
<?php

class Human {
	public $name = 'quidam';
}

class Man extends Human {
	function setName($name) { 
		$this->name = $name;
	}
	
	function getName() { 
		return $this->name;
	}
	
	function __toString() {
		return 'M. '.$this->name;
	}
}

class UnknownSoldier extends Human {
	function __construct() {
		$this->name = 'Unknown';
	}

	function __toString() {
		return 'Soldier '.$this->name;
	}
}

?>
```

It seems that the common class only holds the `$name` property, while child classes has various ways to set the name. Child classes have their own usage of the `$name` (see `__toString()`). As it is, `$name` act as a hard link between the classes. 

It would be cleaner to have different properties in each child class, so as to decouple them, or to move some common accessors in `Human`, to provide some generic way. 

Private properties will naturally need their own local methods for manipulations, as they can't be accessed from anywhere else. 

Protected properties will be accessed by child classes, so methods that access such properties may be located in the parent class or its child. However, the parent class should make some use of that property, such as initializing it, reset it, changing its state.  

Public properties may be accessed from anywhere. When they are in an object but not used from within, then they do not belong to that class but to another one. 

Abstract an final classes are included in this rule.

It is recommended to make sure that properties are at least used once locally. 

## Rule Details

The following patterns are considered warnings:

```php
<?php

class Vehicle {
	protected $unusedLocally = 0;
}

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

