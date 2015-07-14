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


## 规则详情

使用上面提到的任何函数会触发一个警告。

<!--
### 选择

## 什么时候不使用它
-->

## 进一步阅读

* [PHP 陷阱](https://secure.phabricator.com/book/phabflavor/article/php_pitfalls/)
