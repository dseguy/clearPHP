<!-- 性能 -->
# 避免使用运行慢的函数

有些PHP原生函数应该处于速度原因避免使用。它们列在下面。

| 函数 | 替代方法 |
|---|---|
| array\_diff        | 尝试使用 array\_diff\_key, 因为键是唯一的 |
| array\_intersect   | 尝试使用 array\_intersect\_key, 因为键是唯一的 |
| array\_udiff       | 尝试使用 array\_diff\_key, 因为键是唯一的 |
| array\_uintersect  | 尝试使用 array\_intersect\_key, 因为键是唯一的 |
| array\_unique      | 使用 array\_count\_values 和 array\_keys|
| uasort             | 建造一个数组，来不使用u sort|
| uksort             | 建造一个数组，来不使用u sort|
| usort              | 建造一个数组，来不使用u sort|
| in\_array          | 建造一个数组，使它能够被isset()替换 |
| preg\_replace      | 对于简单的替换，用str\_replace()替换 |
| array\_search      | 用array\_key\_exists()来替换 |
| array\_shift       | 用另外一种方式来处理数组，使用array\_pop() |
| array\_unshift     | 用另外一种方式来处理数组，使用array\_push() |
| strstr             | 对于简单的搜索，使用strpos() |
| uniqid()           | 请总是提到entropy (它的第二个参数) |
| array\_walk()      | 使用 foreach($source as &$variable) { } |
| array\_map()       | 使用 foreach($source as &$variable) { } |
| range()            | 你可以使用 [generators](http://php.net/manual/language.generators.overview.php), 来避免在内存中建立数组 |
| is\_null()         | 使用 `=== null` 或其它类似方法                             |
| is\_resource       | 使用 `=== false` 或其它类似方法                            |
| is\_bool()         | 使用 `=== false` 或其它类似方法                            |
| intval()           | 类型转换到 `(int)`                                       |
| floatval()         | 类型转换到 `(float)`                                     |
| strval()           | 类型转换到 `(string)`                                    |
| boolval()          | 类型转换到 `(bool)`                                      |
| settype()          | 类型转换到 `(bool)`, `(string)`, `(int)` 或 `(float)`    |


## 增量操作符

即时它不是一个函数，前置的增量操作符比后置的增量操作符要快，因为后者多了一个内存拷贝。

注意，用`++$i` 替换`$i++` 不是很直接了当的：在任何把结果赋值给一个变量的情况或在一个表达式中使用时，它们不能留着不变或者需要重构。  

```php
<?php

// 安全的替换
for($i = 0; $i < 10; $i++) { 
	//做一些事情
}
$d++; // 单单的一行

// 在替换之前需要审查
$a = $b++;
$c = pow($d++, 2); // 将 $d 提升到平方，而不是把$d 加 1

?>
```

## 规则详情

使用上面提到的任何函数会触发一个警告。 

```php
<?php

// 避免使用array_unique
$distinct = array_unique($incomingArray);

// 使用一个类型的转换
$price = floatval($source['price']);

?>
```
<!--
### 选择
-->
## 什么时候不使用它
这些是一些微观的优化，比起一些架构上的超出本文的范围的优化来。不要开始手动的替换您的代码中所有的例子为更快的方法，而是在写一些新的代码时，请记住这些规则。

当您有对这些函数编码标准的约定时，请保持您的约定的一致性。


## 进一步阅读
* [PHP 陷阱](https://secure.phabricator.com/book/phabflavor/article/php_pitfalls/)
* [++$i 和 $i++ 在PHP中的不同？](http://stackoverflow.com/questions/1756015/whats-the-difference-between-i-and-i-in-php)
