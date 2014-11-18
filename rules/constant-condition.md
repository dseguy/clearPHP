<!-- Good Practices -->
# Constant Condition

Constant conditions signals a debug situation (forcing some rare behavior), a bug or a typo. 

```php
<?php
if (true) { 
	// Store in cache
}
// caching is forced, while it should be configurable

while($x = fetchData()) {

	if (strlen($x) == 0) { break 1;}
	
	// process $x
}
// should be a do ... while() without a break

?>
```

It is recommended to use the master function instead of any alias.


## Rule Details

This rules spots conditional structures which value may be processed even before compiling the code. Such structures should be reviewed.

The following codes are considered a warning:

```php
<?php

// with if or elseif
if (true) { 
	// doSomething()
} elseif (2) {
	// doSomething()
}

// with ternary operator
$x = 0 ? 1 : 2;

// with do...while
do 
	// doSomething()
while (1 == 1);

// with while
while (!false) {
	// doSomething()
}

// with for
for ( ; $x == 2 || true ; ) {
	// doSomething()
}

?>
```

The following pattern is considered legit:

```php
<?php

// SOME_CONSTANT may be configured somewhere
if (SOME_CONSTANT) { 
	// doSomething()
} 

// with for
for ( ; $object->property == 2 ; ) {
	// doSomething()
}


?>
```

<!--
## When Not To Use It



## Further Reading 

* [PHP functions aliases] (http://php.net/manual/en/aliases.php)
-->