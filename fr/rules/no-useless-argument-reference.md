<!-- Good Practices -->
# No Useless Reference Arguments

Arguments may be passed by reference, allowing the called method to modify the content. If the method doesn't modify the content, then passing a reference is useless, as PHP will optimizes the call itself. 

```php
<?php

$user = 'username';
$content = 'Some value';

	function doSomething(&$user, &$content) {
		if (new User($user)->isAllowed()) {
			$content .= ' Modified by doSomething';
		}
	}

?>
```

In the previous example, `$content` is modified and the reference is actually needed. On the other hand, `$user` is only read to build the object, and will not be modified : this reference is useless.

It is recommended to only use references when they are needed.

## Rule Details

The following patterns are considered warnings:

```php
<?php

$user = 'username';
$content = 'Some value';

// here, $content is OK, $user should not have reference
	function doSomething(&$user, &$content) {
		if (new User($user)->isAllowed()) {
			$content .= ' Modified by doSomething';
		}
	}

// here, $array is OK, 
//	     $object should not have reference as it is an object
//      $method should not have a reference as it won't be modified   
	function doSomething(array &$array, Stdclass $object, callable $method) {
		$array[] = 1;
		/* do Something */
	}

?>
```

<!--
### Options

## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically. 

## Further Readings
-->

