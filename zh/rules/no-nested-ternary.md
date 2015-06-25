<!-- 好的实践 -->
# 不要嵌套三元运算

三元运算是一个压缩的 `if then else` 结构。用一行判断就可以处理简单的逻辑分支，十分的方便。

```php
<?php

print 'Result : ' . ( $success ? 'transaction succeded' : 'transaction failed');

?>
```

三元运算是可以嵌套的。但这会降低代码的可读性。

```php
<?php

print 'Result : ' . ( $success ? $christmas ? 'transaction success and you get a gift' : 'transaction success' : 'transaction failed');

?>
```

必须要提到的是：嵌套的三元运算有时不会得到你所期待的结果。例如：

```php
<?php

echo $foo ? 'a' : $bar ? 'b' : 'c';

?>
```

以下是 `$foo` 和 `$bar` 的四种逻辑组合的结果：

| `$foo` | `$bar` | result |
|--------|--------|--------|
| true   | true   | b      |
| true   | false  | b      |
| false  | true   | b      |
| false  | false  | c      |

所以，建议大家不要使用嵌套的三元运算。

## 规则细节

三元运算是很好的。但是嵌套它就不那么舒服了。

如下代码会被视为警告：

```php
<?php

$foo ? 'a' : $bar ? 'b' : 'c';

$foo ?: $bar ? 'b' : 'c';

$foo ?: $bar ?: 'c';

?>
```

如下代码是正规用法：

```php
<?php

$a = $bar ? 'b' : 'c';
$d = $foo ? 'a' : $b;

if ($foo) {
	$d = 'a';
} elseif ($bar) {
	$d = 'b';
} else {
	$d = 'c';
}

?>
```

<!--
## When Not To Use It
Never


## Further Reading
-->

## 译者

* [cxbig](http://github.com/cxbig)
