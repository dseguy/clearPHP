<!-- Performances -->
# No Functioncall In Loop

Loops are a way to execute the same instructions multiple times. That ability makes them prime candidate for optimization : the less process in a loop, the fastest the loop performs. 

```php
<?php

$x = range(1,10);
for($i = 0; $i < count($x); $i++) {
	// doSomething with $i
}
	
?>
```
In the above statement, `$i < count($x)` is the terminal clause. It will be called after each iteration to check if the loop shall continue. Each time, it will count the number of elements in `$x`, even if this variable hasn't been changed. Calling `count($x)` may be saved by processing it before the loop, then only checking `$i` against a static value. 

```php
<?php

$x = range(1,10);
$count = count($x);
for($i = 0; $i < $count; $i++) {
	// doSomething with $i
}
	
?>
```
This second code will do the same as the first, but speed will be dramatically increased. 

As a general rule, anything inside the loop (here `doSomething with $i`), in the terminal clause or in the incrementation clause (second and third argument to `for`, are worth checking for any operation that will not be affected by `$i`. If it is always the same, then it should be preprocessed. 

## Rule Details

The following code is considered a warning:

```php
<?php

$x = range(1,10);
$count = count($x);
for($i = 0; $i < $nb; $object->methodCall()) {
	// doSomething with $i and not $object
}

$x = range(1,10);
$count = count($x);
for($i = 0; $i < $count; $i++) {
	$a = $object->methodCall(); // This may be processed once only
	$total += $i * $a;
}
	
?>
```

The following pattern is considered legit:

```php
<?php

// here, the condition changes as the loop is process. This is needed
$x = range(1,10);
$j = array();
for($i = 0; $i < count($j); $i++) { 
	// doSomething with $i and $j
}
	
?>
```

<!--
## When Not To Use It



## Further Reading

-->