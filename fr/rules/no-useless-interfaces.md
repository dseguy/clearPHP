<!-- Good Practices -->
# No Useless Interfaces

Interfaces are a way to specify methods that a class must implements, leaving the actual implementation to the class. 

```php
<?php

interface area {
	function getArea();
}

class Square implements Area {
	private $side; 
	
	public function getArea() {
		return $this->side ** 2;
	}
}
?>
```

Interfaces may also be used in `instanceof` structures and `Typehint`, to enforce that variables or arguments are correct objects, providing public access to a certain set of methods. 

```php
<?php

if ($circle instanceof Area) {
	// area calculation are available from the object
	return $circle->getArea();
} else {
	useOtherWayToGetArea($circle);
}

function getRadiusOfEquivalentCirle(Area $shape) {
	return sqrt($shape->getArea()/M_PI);
}

?>
```

When interfaces are only used to define classes (or other interfaces), they may actually be removed once the class is coded : they are used as guideline to build the final class. As such, they are useless interfaces.

On the other hand, interfaces mentioned in `instanceof` or `Typehint` are providing control over objects and their nature, helping to detect unfitting values. They play an active role during code execution. 


It is recommended to check that interfaces are used in  `instanceof` or `Typehint` structure, or consider removing them. 

## Rule Details

This is considered a warning : 

```php
<?php

interface Area {
	function getArea();
}

interface SuperArea extends Aread{
	function getSuperArea();
}

class Square implements Area {
	private $side; 
	
	public function getArea() {
		return $this->side ** 2;
	}

	public function getSuperArea() {
		return $this->side ** 3;
	}
}

// only definition usage
// no instanceof 
// no typehint

// Do not confuse useless interface with unused interface (defined but never used by a class or an interface

?>
```

The following are considered legit : 

```php
<?php

// based on previous classes and interfaces

if ($circle instanceof Area) {
	// area calculation are available from the object
	return $circle->getArea();
} else {
	useOtherWayToGetArea($circle);
}

// Area is used as Typehint
function getAreaOrSuperArea(Area $shape) {

	// SuperArea is spotted here
	if ($shape instanceof SuperArea) {
		return $shape->getSuperArea();
	} else {
		return $shape->getArea();
	}
}

?>
```

<!--
## When Not To Use It
Please, always use it.
 -->

## Further Reading

* [Interfaces](http://php.net/manual/en/language.oop5.interfaces.php)
* [Type Hinting](http://php.net/manual/en/language.oop5.typehinting.php)
* [Instance of](http://php.net/manual/en/language.operators.type.php)
