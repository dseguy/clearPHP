<!-- Good Practices -->
# Unresolved instanceOf

The `instanceof` operator checks that an object is of a class, or has this class in its ancestors.

```php
<?php

class A { }
class B extends A {}

$b = new B();

var_dump($b instanceof A); // true
var_dump($b instanceof B); // true
var_dump($b instanceof C); // false
?>
```
In the example here, `C` doesn't exist. The operator doesn't tell the difference between "C doesn't exist" and "$b is not of class C". No error is reported. 

As `instanceof` is often used in condition, this will lead to dead code (or to constantly used code). This is not desirable. 

It is recommended to make sure that the class used in the left part of the `instanceof` operator is always valid.

## Rule Details

The following patterns are considered warnings:

```php
<?php

// various sources for unexisting class
$a instanceof UnexistingClass;

$a instanceof ClassWithASpelllingMistake;

$a instanceof ClassActuallyInAnotherNamespace;

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

