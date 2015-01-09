<!-- Good Practices -->
# No References On Objects

Since PHP 5, objects are always passed by reference whenever calling a method or a function. There is no need to add the `&` operator to create a reference. The object will stay in the initial context, and will be modified in any called context. 

```php
<?php

// Object has property
$o = new Object();

f($o);

// function accept 
function f($object) {
	$object->property = 2;
}

print $o->property; // 2

// calls are identical for objects
call_user_func_array('f', array($o));
call_user_func_array('f', array(&$o));

?>
```

This would be totally different for scalar values, which depends on `&` to be passed by value or by reference. 

It is recommended never to use reference on objects.


## Rule Details


The following code is considered a warning:

```php
<?php

$o = new Object();

// Typehint makes the reference useless
function f(Object &$a) {}

foreach($arrayOfObject as &$object) {
	$object->alter();
}

?>
```

<!--
## When Not To Use It



## Further Reading 
-->
