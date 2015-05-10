<!-- Good Practices -->
# No Mixed Loops

`for` loops makes usage of local counters and requires a incrementation expression. Mixing the counters from one loop into the other is confusing at best. 

```php
<?php

for ($i = 0; $i < 10; $i++) {
	for ($j = 0; $j < 20; $i++) {
		// doSomething with $i and $j
   }
}

?>
```

It is recommended to always keep loops's counter separated. In case they have an impact on each other, make the change obvious in the body of the loops.


## Rule Details

The following code is considered a warning:

```php
<?php

for ($i = 0; $i < 10; $i++) {
	for ($j = 0; $j < 20; $i++) {
		// doSomething
   }
}

?>
```


The following pattern is considered legit:

```php
<?php

// $i incrementation obviously depends on the second loop
for ($i = 0; $i < 10; ) {
	for ($j = 0; $j < 20; ) {
		$i++;
		print "$i $j\n";
		// doSomething
   }
}

?>
```

<!--
## When Not To Use It

## Further Reading 

-->