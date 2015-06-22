<!-- 好的实践 -->
# 使用 Foreach

`foreach` 指令在 PHP 4 就被推荐使用：这是一个循环指令，可以遍历数据源中的所有元素。  
`foreach` 在多年内不断的进化，现在它可以用来遍历任何带有迭代器接口的对象。

```php
<?php

foreach ($source as $key => $element) {
  // doSomething with the element
}

?>
```

更早的遍历指令，如 `for` 和 `while...each`：

```php
<?php

while(list($key, $element) = each($source)) {
  // doSomething with the element
}

// 通常用于已排序的数组。对带有 `hash` 索引的数组不适用
$count = count($source);
for($i = 0 ; $i < $count; $i++) {
  // doSomething with the $source[$i]
}

?>
```

虽然这两种方案仍然可以使用，甚至在一些特定场合会更快，但还是推荐尽量使用 `foreach`。

`foreach` 控制循环遍历数组，无论其大小。它避免了在 `for` 循环中使用 `count()`。  
而且将元素的索引和值直接赋给变量，易于操作。

另外，`foreach` 可以用于更复杂的结构，包括迭代器或生成器。

建议尽量使用 `foreach` 来处理数组和完整的数据源。

## 规则细节

如下例子将是为一个警告：

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

一下例子被视为正规用法：

```php
<?php

// 无数组的for循环
for ($i =0; $i < $nb; $i++) {
	$div = $nb % $i;
}

// 无大小定义的来源 (如 SQL 结果)
// 同时，这种方法可以避免将整个源数据加载到内存（避免内存超限）
while($row = $pdo->fetchRow()) {
    // doSomething with the element
}

?>
```
<!--
### Options

## When Not To Use It
-->

## 延伸阅读
* [Iterator](http://php.net/manual/zh/class.iterator.php)
* [PHP generators](http://php.net/manual/zh/language.generators.overview.php)
* [Foreach](http://php.net/manual/zh/control-structures.foreach.php)

## 译者

* [cxbig](https://github.com/cxbig)
