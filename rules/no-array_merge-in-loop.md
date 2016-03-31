<!-- Good Practices -->
# No Array_merge In Loops

`array_merge` accepts an arbitrary number of arrays as argument. Calling this function once with all the arguments is faster than calling the same function inside a loop, each time with one argument. 

Besides, `array_merge` particularly slow and memory intensive when it is used in a loop. 

`array_merge` is particularly slow and memory intensive when it is used in a loop. 

```php
<?php

$result = array();
foreach ($source as $list) {
  $result = array_merge($result, $list);
}

?>
```

At each iteration, PHP copies the array into another temporary array, leading to as many temporary allocation as there are elements in the original `$source` array. Each time, the memory allocated will be more than the previous one, accelerating the memory usage. 

Beside the memory allocation, the copy of the data from one temporary value to the other will also consume time and processing power. 

The solution to this problem is to call `array_merge` once with all its arguments. In this case, or if the number of arrays to be merged is unknown at development time, using variadic functions or `call_user_func_array` is also much more efficient.

```php
<?php

//$source is a array of arrays : $source[0] = [ /**/ ];

// Hard-coded version, when the all elements from $source are known
$result = array_merge($source[0], $source[1], $source[2]);

// Dynamic version : 
// PHP 5.6 and later
$result = array_merge(...$source);

// PHP 5.5 and before
$result = call_user_func_array('array_merge', $source);

?>
```

Actually, using `call_user_func_array` or `...` is faster for several other array functions. Note that memory impact, such as explained for `array_merge` may be lower when the function removes data : 

* `array_merge_recursive`
* `array_merge`
* `array_replace_recursive`
* `array_replace`
* `array_diff`
* `array_diff_assoc`
* `array_diff_key`
* `array_diff_uassoc`
* `array_diff_ukey`
* `array_intersect`
* `array_intersect_assoc`
* `array_intersect_key`
* `array_intersect_uassoc`
* `array_intersect_ukey`
* `array_udiff`
* `array_udiff_assoc`
* `array_udiff_uassoc`
* `array_uintersect`
* `array_uintersect_assoc`
* `array_uintersect_uassoc`
* `max`
* `min`
* `wddx_serialize_vars`
* `wddx_add_vars`
* `array_push` [1]
* `array_unshift` [1]
* `print`
* `fprintf`

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
* [array_merge] (http://php.net/array_merge)
* [call_user_func_array](http://php.net/call_user_func_array)
* [Variadic](http://php.net/functions.arguments#functions.variable-arg-list)
