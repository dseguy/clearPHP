<!-- Good Practices -->
# No Array_merge In Loops

`array_merge` is particularly slow and memory intensive when it is used in a loop. 

```php
<?php

$result = array();
foreach ($source as $list) {
  $result = array_merge($result, $list);
}

?>
```

At each iteration, PHP will copy the array into another temporary array, leading to as many temporary allocation as there are elements in the original `$source` array. Each time, the memory allocated will be more than the previous one, accelerating the memory usage. 

Beside the memory allocation, the copy of the data from one temporary value to the other will also consume time and processing power. 

The solution to this problem is to call `array_merge` once with all its arguments. In this case, or if the number of arrays to be merged is unknown at development time, using variadic functions or `call_user_func_array` is also much more efficient.

```php
<?php

$result = array_merge($source[0], $source[1], $source[2]);

// PHP 5.6 and later
$result = array_merge(...$source);

// PHP 5.5 and before
$result = call_user_func_array('array_merge', $source);

?>
```

## Rule Details

The following snippets are considered a warning:

```php
<?php

foreach($a as $b) {
	$c = array_merge($c, $b);
}

for($i = 0; $i < 10; $i++) {
	$c = array_merge($c, $array[$i]);
}

while(count($a) > 0) {
	$c = array_merge($c, array_pop($a));
}
	
?>
```
<!--
### Options

## When Not To Use It
-->

## Further Readings
* [array_merge() in Incredibly Slow When Merging A List of Arrays](https://secure.phabricator.com/book/phabflavor/article/php_pitfalls/#array-merge-in-incredibl)
* [array_merge] (http://php.net/manual/en/function.array-merge.php)
* [call_user_func_array](http://php.net/manual/en/function.call-user-func-array.php)
* [Variadic](http://php.net/manual/en/functions.arguments.php#functions.variable-arg-list)