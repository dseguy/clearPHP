<!-- Good Practices -->
# No Catch Overwrite

`try ... catch` is the structure designed to handle errors, emitted as `Exception`. Code will be run in the `try` block, and if some `Exception` is emitted, the class of the `Exception` will route it to the right `catch` block for processing. 

`catch` blocks define an Exception type, and a variable that will hold the Exception object. 

```php
<?php

$e = 1;
try {
	/* some code */
} catch (Exception $e) {
	process($e->getMessage());
}

?>
```

The `catch` variable, here `$e`, will overwrite any already existing variable, if an Exception is emitted. 

It is recommended to avoid overwriting variables with a catch block.

## Rule Details

The following illustrate both right and wrong situations : 

```php
<?php

// $e is already defined
$e = 1;

try {
	/* some code, may be using $e too */
} catch (Exception $e) {
	// $e is wrong
	process($e->getMessage());
} catch (otherException $f) {
	// $f is OK
	process($f->getMessage());
}


?>
```

<!--
## When Not To Use It


## Further Reading

-->