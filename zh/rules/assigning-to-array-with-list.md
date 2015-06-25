<!-- PHP 手册 -->
# 用 List 给数组赋值

PHP语言把 `list` 打造成可以接受任何数据容器来做为参数。  
大多数时候，这些参数是变量。但是，使用数组也是很不错的选择。

```php
<?php

$info = array('arabica', 'brown', 'caffeine');

list($a[0], $a[1], $a[2]) = $info;

var_dump($a);

?>
```

值会赋给正确的索引，但是 `list` 的赋值顺序是从右到左（如下数组所示）。并不是按照大多数时候所期待的从左到右。

```
array(3) {
  [2]=>
  string(8) "caffeine"
  [1]=>
  string(5) "brown"
  [0]=>
  string(6) "arabica"
}
```

如果顺序对于结果数组是很重要的，推荐使用 `array_reverse` 给结果数组反转，或者使用其他方法构造数组。

<!--
The following patterns are not considered warnings:

```php
<?php


?>
```


### Options

## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically.
-->

## 延伸阅读
* [list()](http://php.net/manual/zh/function.list.php)
