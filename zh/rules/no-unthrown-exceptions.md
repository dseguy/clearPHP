<!-- 好的实践 -->
# 不留无效的Exceptions

PHP提供了 **例外**：`Exception`。  
所有 **例外** 被定义为继承 PHP 的根 `Exception`，然后当错误需要被报告的时候抛出。

```php
<?php

class unusedException extends \Exception {}

class divisionByZero extends \Exception {}

$a = 1;
$b = 0;

if ($b === 0) {
	throw new divisionByZero();
}

print $a / $b."\n";

?>
```

这里建议删除没有被使用的 **例外**：`unusedException`。

<!--
### Options

## When Not To Use It

## Further Readings
*[Arrays](http://php.net/manual/en/language.types.array.php)

-->

## 译者

* [cxbig](https://github.com/cxbig)
