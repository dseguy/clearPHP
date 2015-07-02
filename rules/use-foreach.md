<!-- Good Practices -->
# Use Foreach

`foreach` instruction has been introduced in PHP 4 : it s a loop that will review all element in the source provided. `foreach` has evolved over the years, and is now able to loop over any object that implements the `Iterator` interface. 

```php
<?php

foreach ($source as $key => $element) {
  // doSomething with the element
}

?>
```
Older ways of building such loops include the usage of the `for` loop, and the `while...each` loop. 

```php
<?php

while(list($key, $element) = each($source)) {
  // doSomething with the element	
}

// often used with indexed arrays, as hashes may be more cumbersome
$count = count($source);
for($i = 0 ; $i < $count; $i++) {
  // doSomething with the $source[$i]	
}

?>
```

While the two alternatives still available, and may even be faster in edge cases, it is recommended to always use `foreach`. 

`foreach` takes charge of looping over the array, whatever its size. It prevents the usage of `count()` in the for() loop, and assign the values into handy variables.

Besides, foreach may be used with more complex structures, including iterators or generators. 

It is recommended to always use foreach over arrays or finished sources. 

## Rule Details

The following snippets are considered a warning:

```php
<?php

while(list($key, $element) = each($source)) {
  // doSomething with the element	
}

$count = count($source);
for($i = 0 ; $i < $count; $i++) {
  // doSomething with the $source[$i]	
}
	
?>
```

The following snippets are considered legit:

```php
<?php

// No array involved
for ($i =0; $i < $nb; $i++) {
	$div = $nb % $i; 
}

// undefined size source (sql result)
// also, this will avoid dumping all result in memory
while($row = $pdo->fetchRow()) {
  // doSomething with the element	
}

?>
```
<!--
### Options

## When Not To Use It
-->

## Further Readings
* [Iterator](http://php.net/class.iterator)
* [PHP generators](http://php.net/language.generators.overview)
* [Foreach](http://php.net/control-structures.foreach)
