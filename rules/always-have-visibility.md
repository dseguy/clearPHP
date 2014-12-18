<!-- Good Practices -->
# Always Has Visibility

For compatibility reasons, PHP allows methods and properties to be defined without visibility : `public`, `protected` or `private`. By default, methods and properties are defined as `public`, making them available to all other objects without restriction.

It is recommended to always set the visibility.

## Rule Details

This rule is aimed at avoiding omitting visibility for properties and methods.

The following patterns are considered warnings:

```php
<?php

abstract class x {
	static $staticProperty;
	var $varProperty;

	function defautVisibilityMethod() {}
	static function defautVisibilityStaticMethod() {}
	final function defautVisibilityFinalMethod() {}
	abstract function defautVisibilityAbstractMethod();
	
}

?>
```

The following patterns are not considered warnings:

```php
<?php

abstract class x {
	static protected $staticProperty;
	public $varProperty;

	public function defautVisibilityMethod() {}
	static protected function defautVisibilityStaticMethod() {}
	final private function defautVisibilityFinalMethod() {}
	abstract public function defautVisibilityAbstractMethod();
	
}

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

