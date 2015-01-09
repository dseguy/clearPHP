<!-- Good Practices -->
# Avoid Redefining Properties

At least, properties should be used in the class or trait where they are defined. 

Check the code below : `$lock` is defined in a class, and manipulated in another. Locking the vehicle, 

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
}

?>
```

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

