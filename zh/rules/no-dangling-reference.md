<!-- 可能的错误 -->
# 没有留坠的指引

在一个foreach的循环中，一个变量被用来在循环过程中指引数组中的每个元素。如果这个变量，为了能就地修改的目的，被声明为一个指引，这个指引变量在循环结束后还是会存在。当这个最后的指引在后面再次使用时，它将会把它的值运用到数组的最后一个元素。

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

在这个例子中，`$array[1]` 最终会被赋值为`'d'`, 第二个循环的数组中的最后的一个值。任何对`$a`的赋值也都会对数组`$array`有影响。

`
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
`

## 规则细节

这条规则针对在循环后没有unset循环的指引的代码的使用。

下面这样的代码视为一个警告：

```php
<?php
foreach (array(1, 2, 3, 4) as &$value) {
    $value = $value * 2;
}
$other_value *= 2;
unset($value); // 不要等得太晚才移掉$value
?>
```


下面的代码片段是被视为合法的：

```php
<?php
foreach (array(1, 2, 3, 4) as &$value) {
    $value = $value * 2;
}
unset($value);
?>
```

<!--
## 什么时候该不使用

-->

## 进一步的阅读

* [PHP 中的 foreach](http://php.net/manual/en/control-structures.foreach.php)