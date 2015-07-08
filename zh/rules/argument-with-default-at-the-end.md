<!-- PHP 手册 -->
# 缺省参数放在最后

当定义一个方法时，对参数提供一个缺省的值是可能的：值需要在参数的名字后面加上等于号和那个缺省值。

```php
<?php

function withoutDefault($a) {} 
function withDefault($a = 1) {} 

?>
```

在上面的例子中，函数`withDefault` 有一个参数，它的缺省值为`1`. 这样，这个参数可以在调用时省略掉，而它将会在函数中以值为1出现。PHP 使用这样的参数来定义像`htmlentities` 或 `array_unique` 的函数. 

PHP 只接受有缺省值的参数在参数列表的最后的情况。像这样：

```php
<?php

function withDefault($a, $b, $c = 1, $d = 2 ) {}
function withDefault2($a, $b, $c = 1, $d = 2, $e = 'd' ) {}

?>
```

上面的两个函数，分别地，两个和三个参数和两个必须参数。通过这样的方式，它们可以只通过两个参数来调用，那些最后的参数将被自动的填入缺省值。

这里的陷阱是PHP并不按照手册上的要求来严格限制。给任何顺序的参数定义一个缺省值并顺利编译是可能的。错误将会在运行时出现。

```php
<?php

function f($a, $b = 1, $c ) {
	echo $a, $b, $c, "\n";
}

f(1,2,3); // 显示 123
f(1,3);   // 显示 13 和一个 错误

?>
```

PHP 将会仍然按照输入参数的顺序赋值。当它没有值再用时，它将会试图在定义中找一个缺省值，但是没有这个缺省值，它会确定这个参数是忘掉了。

这样，检查只有参数列表的最后的参数拥有缺省值是非常重要的。 

## 规则详情

这个规则运用于PHP手册的指令但没有在PHP解释器里实现。

下面的代码视为警告：

```php
<?php

function f($a = 1, $b) {}

function f($a = 1, $b, $c = 3) {}

function f($a = 1, $b, $c = 3, $d) {}

?>
```

项目的代码不会视为警告：

```php
<?php

function f($a = 1, $b = 2) {}

function f($a = 1, $b = 2, $c = 3) {}

function f($a, $b, $c, $d) {}

?>
```

<!--
### 选择
-->

## 什么时候不用它When Not To Use It
永远都使用它 

## 进一步的阅读
* [函数参数](http://php.net/manual/functions.arguments.php) (查看第5个用例关于不正确地使用函数参数)
