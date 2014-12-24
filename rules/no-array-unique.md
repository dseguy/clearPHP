<!-- Performances -->
# No `array_unique`

`array_unique` function is a native function that will extract distinct values in an array. `array_count_values` is also a native function that will extract distinct values in an array, and count the number of occurrences.

`array_count_values` actually does a lot more work than `array_unique` by providing a count of the distinct values, on top of finding them. On the other hand, extracting the keys from the result of `array_count_values` removes the counts, and is the same result than `array_unique`.

```php
<?php

$a = array('a', 'b', 'c', 'b', 'c', 'c');

print_r(array_unique($a));
//array('a', 'b', 'c');

print_r(array_keys(array_count_values(($a)));
//array('a', 'b', 'c');

?>
```

In fact, `array_count_values` is a lot faster than `array_unique`. It may be twice as fast for small arrays (with tens of values), and it get even faster as the size of the array grows. 

The limitations are that `array_count_values` can only count `string` and `integer` values (as the PHP error will show if some other type is used), and `array_unique` includes a sorting option.

It is also possible to use other fast alternatives : `foreach` with `array_keys`, or `array_flip`.

## Rule Details

The following code is considered a warning:

```php
<?php

$a = array('a', 'b', 'c', 'b', 'c', 'c');

$b = array_unique($a);

?>
```

The following code is considered legit:

```php
<?php

$a = array('a', 'b', 'c', 'b', 'c', 'c');

$b = array_keys(array_count_values(($a));

?>
```

<!--
## When Not To Use It
-->

## Further Reading
* [array_unique](http://www.php.net/array_unique)
* [array_count_values](http://www.php.net/array_count_values)
* [array_keys](http://www.php.net/array_keys)
* [array_flip](http://www.php.net/array_flip)
* 
