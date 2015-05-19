<!-- PHP Manual -->
# 避免使用函数别名（Function Alias）

_中文版翻译可能会保留一些特定词汇_

PHP存在大量的函数别名：同一个函数可以有多个别名。例如 `is_int`，还可以用 `is_integer` 或者 `is_long`。
使用 `is_int` 和 `is_integer` 都可以。但是，`is_long` 属于对旧名的延续性支持，它将会在后续版本中被移除。

推荐统一使用主函数名替换所有别名。


## 规则细节

本规则针对所有正在被使用的别名。  
如使用别名，当 `PHP` 解析该代码时会产生一个 `E_WARNING`，其内容是建议你使用主函数名。  
所有函数别名在 `PHP手册` 都会被列出，并可以找到详细描述，  
例如：它的主函数名是什么、__不推荐使用__标记和它在未来的某个PHP版本将会被移除等信息。


如下的例子将会触发 `E_WARNING`：

```php
<?php
if (is_long($value)) {
	// DoSomething()
}

if (is_integer($value)) {
	// DoSomething()
}
?>
```


如下例子被认为是正规的使用方法：

```php
<?php

if (is_int($value)) {
	// DoSomething()
}

?>
```

<!--
## When Not To Use It

-->

## 深入阅读

* [PHP 函数别名列表](http://php.net/manual/zh/aliases.php)


## 译者

* [Buck CHEN](https://github.com/cxbig)
