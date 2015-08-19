<!-- 最佳实践 -->
# 常量条件

常量条件预示着一个调试情况（强制某些少有的行为），一个bug或一个笔误。

```php
<?php
if (true) { 
	// 存在缓存中
}
// 缓存被强制了，而它应该是可以设置的

while($x = fetchData()) {

	if (strlen($x) == 0) { break 1;}
	
	// 处理 $x
}
// 应该是一个do ... while() 并且没有break

?>
```

使用常量条件的循环，通常包含一个退出指令，以允许它们终止而不影响整个应用。这样的循环也许可以将退出函数更加明显的方式重写，在循环的条件中。

```php
<?php

while(true) {
	waitForEvent();
	
	// 退出函数需要放置于循环条件中。
	if (receivedQuitSignal()) {
		break 1;
	}
}

?>
```

然而在条件中使用常量不会被视为常量条件：这样的常量可以是条件式常量（它们的值可能在程序开始时动态地定义，或来自一个外置的文件），或甚至拥有动态的值（比如魔力常量的情况--magic constants）。常理条件将会使用字面常量值。

在流程指令中使用非常量条件是强烈推荐的。


## 规则详情

这个规则定位到常理条件，它甚至可能在编译时之前处理。这样的结果是应该被审核的。

下面的代码被视为一个警告：

```php
<?php

// 用 if 或 elseif
if (true) { 
	// doSomething()
} elseif (2) {
	// doSomething()
}

// 使用 ternary 操作符
$x = 0 ? 1 : 2;

// 使用 do...while
do 
	// doSomething()
while (1 == 1);

// 使用 while
while (!false) {
	// doSomething()
}

// 使用 for
for ( ; $x == 2 || true ; ) {
	// doSomething()
}

?>
```

下面的代码是被视为合法的：

```php
<?php

// SOME_CONSTANT 也许在其他地方设置了
if (SOME_CONSTANT) { 
	// doSomething()
} elseif (basename(__FILE__) == 'index.php') {
	// __FILE__ is a dynamic constant
}

// 使用 for
for ( ; $object->property == 2 ; ) {
	// doSomething()
}

// 这里，, 条件在 case 从句里面
switch (true) {
	case $a : 
		// doSomething()
		break;
	
	case $c == $d; 
		// doSomething()
		break;
	
	default : 
}

?>
```

<!--
## 什么时候不使用



## 进一步阅读 

* [PHP 函数别名] (http://php.net/manual/aliases.php)
-->
