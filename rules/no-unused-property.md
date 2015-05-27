<!-- Good Practices -->
# No Unused Property

Properties are defined in a class, or created when needed during execution. Properties that are not used anywhere in the code are most likely useless. Such properties consume memory, use code space and may create confusion.

As a simple check, any property only used once in a context should be checked. 

It is recommended to check that properties are used more than once in their class of definition.

## Rule Details

This rule is aimed at eliminating unused variables or arguments.

The following patterns are considered warnings:

```php
<?php

class foo {
	private $unused = 2;
	
	function bar() {
		$this->assignedOnly = 2;
	}
}
?>
```

The following patterns are not considered warnings:

```php
class foo {
	public $used = 2;
	
	function bar() {
		$this->assignedOnly = 2;
	}
}

$foo = new foo();
$foo->used = 4;
```

<!--
### Options

## When Not To Use It

If you don't want to be notified about unused variables, you can turn this rule off.
-->
