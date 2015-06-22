<!-- PHP 手册 -->
# 所有的参数名保持唯一

当定义一个PHP方程的时候，多个参数可以使用同样的名字。

```php
<?php

function f($a, $a, $a) {
	echo $a;
}

f('b', 'c', 'd'); // prints 'd'

?>
```

函数被调用时，变量会根据定义的顺序被赋值，后一个传入的值会覆盖前一个。

```php
<?php

function f($a, $b, $a) {
	echo $b.$a;
}

f('e', 'f', 'g'); // prints 'fg'

?>
```

推荐使用不同的名字定义函数变量。

## 规则细节

以下例子将会触发PHP警报：

```php
<?php

function f($b, $a, $a) { /**/ }

function f($a, $b, $a) { /**/ }

function f($a, $a, $a) { /**/ }

function f(Stdclass $a, $a) { /**/ }

function f(Stdclass $a, $a = 2) { /**/ }

function f(Stdclass $a, &$a) { /**/ }

?>
```

以下例子被认为是正规的使用方法：

```php
<?php

function f($a, $b, $c) { /**/ }

?>
```
<!--
### Options
-->

## 什么时候使用此规则

永远使用这个规则。

<!--
## Further Readings
-->
