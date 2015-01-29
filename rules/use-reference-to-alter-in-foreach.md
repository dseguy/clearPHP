<!-- Performances -->
# Use Reference To Alter In Foreach

`foreach` loops starts by making a copy of the source. This way, the source may be modified without disturbing the loop. 

When the `foreach` has to modify values in the source, it is recommended to use a reference, instead of using index to change the value. 

```php
<?php

$numbers = range(0, 100);

// double each elements
foreach($numbers as &$number) {
	$number *= 2;
}


// double each elements (Bad example)
foreach($numbers as $id => $number) {
	// changing in the source this way is slow
	$numbers[$id] *= 2;
}

// 
?>
```

## Rule Details

The following are considered a warning : 

```php
<?php

foreach($source as $id => $element) {
	// changing in the source this way is slow
	$numbers[$id] = processElement($element);
}

?>
```

The following pattern is considered OK :

```php
<?php

// double each elements
foreach($source as &$element) {
	$element = processElement($element);
}

// use $source[$id] for reading
foreach($source as $id => &$element) {
	$element = processElement($element, $source[$i]);
}

?>
```
<!--
### Options
when static or self call will be different 

## When Not To Use It

If default is not always necessary, you may disable this rule.

## Further Reading
* []()
-->
