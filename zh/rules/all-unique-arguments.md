<!-- PHP 手册 -->
# 全部唯一参数

当定义一个PHP方法时，多个参数可能使用同一个名字。 

```php
<?php

function f($a, $a, $a) {
	echo $a;
}

f('b', 'c', 'd'); // 输出 'd'

?>
```
输入的值被按照方法定义中的参数的顺序赋值：最后一个会复写前面的一个。 

```php
<?php

function f($a, $b, $a) {
	echo $b.$a;
}

f('e', 'f', 'g'); // 输出 'fg'

?>
```

建议永远都使用唯一的不同的参数变量名。

## 规则详情

下面的模式被视为警告：

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

下面的模式不会被视为警告：

```php
<?php

function f($a, $b, $c) { /**/ }

?>
```
<!--
### Options
-->
## 什么时候不用它
永远都用

<!--
## Further Readings
-->
