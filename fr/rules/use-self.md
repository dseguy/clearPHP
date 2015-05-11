<!-- Good Practices -->
# Use Self

`self` is a PHP keyword that represent the current class. Thus, the following are all identical : 

```php
<?php

namespace x\y;

class theClass {
	const a = 1;
	
	public function y() {
		echo self::a."\n";	
		echo theClass::a."\n";	
		echo \x\y\theClass::a."\n";	
	}
}

$z = new z();
$z->y();

?>
```

Of course, full namespaced name is both longer to write and harder to read. The class name is usually longer than `self` (though not all the time, of course). 

`self` keyword will be solved by the PHP interpreter at compile time, with little penalty on processing speed. It will also be handy when refactoring, as there is no more need to change the hardcoded name of the class in the code. 

There are some edge cases where the name of the class will have a different behavior than the `self` keyword : the former will propagate the calling class name, while the class name will actually replace it with itself. 

```php
<?php
class A {
    static function foo() {
        echo get_called_class();
    }
}
class B extends A {
    static function bar() {
        self::foo();
    }
    static function baz() {
        B::foo();
    }
}
class C extends B {}

C::bar(); //C
C::baz(); //B
?>
```
// example quoted from Artefacto

## Rule Details

The following are considered a warning : 

```php
<?php

class theClass {
	const a = 1;
	
	public function y() {
		echo theClass::a."\n";	
		echo \x\y\theClass::a."\n";	
	}
}


?>
```

The following pattern is considered OK :

```php
<?php

class theClass {
	const a = 1;
	
	public function y() {
		echo self::a."\n";	
	}
}

?>
```
<!--
### Options
when static or self call will be different 

## When Not To Use It

If default is not always necessary, you may disable this rule.
-->

## Further Reading
* [self:: vs className:: inside static className metods in PHP](http://stackoverflow.com/questions/3481085/self-vs-classname-inside-static-classname-metods-in-php)
