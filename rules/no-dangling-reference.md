<!-- Potential errors -->
# No dangling references

In a foreach loop, a variable is used for looping through the array. If this variable is made into a reference for on the spot modification purpose, the reference to the last element will survive after the end of the loop. When this last reference is reused later, it will apply to the last element of the array. 

```php
<?php
$array = array('a', 'b');
$array2 = array('c', 'd');

foreach ($array as &$a);
foreach ($array2 as $a);

print_r($array);
print_r($array2);
?>
```

In this example, `$array[1]` finally get assigned with the value `'d'`, which is the last value in the second loop. Any assignation to `$a` would affect `$array` too.

```
Array
(
    [0] => a
    [1] => d
)
Array
(
    [0] => c
    [1] => d
)
```

## Rule Details

This rule targets code that doesn't unset the loop's reference after usage. 

The following code is considered a warning:

```php

foreach (array(1, 2, 3, 4) as &$value) {
    $value = $value * 2;
}
$other_value *= 2;
unset($value); // don't wait too long to remove $value
```


The following pattern is considered legit:

```php
foreach (array(1, 2, 3, 4) as &$value) {
    $value = $value * 2;
}
unset($value);
```

<!--
## When Not to Use It

-->

## Further Reading

* [foreach in PHP](http://php.net/manual/en/control-structures.foreach.php)