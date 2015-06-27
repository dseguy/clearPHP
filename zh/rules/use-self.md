<!-- Good Practices -->
# 使用Self

`self` 是PHP中的一个关键字，用来表示当前的类。如下的用法效果都是一样的：

```php
<?php

namespace x\y;

class theClass {
	const a = 1;

	public function y() {
		echo self::a."\n";
		echo theClass::a."\n";
		echo \x\y\theClass::a."\n";
	}
}

$z = new z();
$z->y();

?>
```

当然，完整的命名空间又长又难以阅读，很多时候类的名字比 `self` 长的多。

`self` 关键字会在PHP解析器编译代码的时候被替换为实际的名字，当然这会占用一点系统的性能。
但是，使用这种方式在代码迭代中是非常方便的。当类名改变等变化发生的时候，你不需要再对其作出修改。

这里有个例外，在有类的继承的情况下，使用类的名字和使用 `self` 关键字所得到的结果不一样。如下例：

```php
<?php
class A {
    static function foo() {
        echo get_called_class();
    }
}
class B extends A {
    static function bar() {
        self::foo();
    }
    static function baz() {
        B::foo();
    }
}
class C extends B {}

C::bar(); //C
C::baz(); //B
?>
```
// 这个例子摘自 Artefacto

## 规则细节

如下用法被视为一个警告：

```php
<?php

class theClass {
	const a = 1;

	public function y() {
		echo theClass::a."\n";
		echo \x\y\theClass::a."\n";
	}
}


?>
```

如下被视为正规的用法

```php
<?php

class theClass {
	const a = 1;

	public function y() {
		echo self::a."\n";
	}
}

?>
```
<!--
### Options
when static or self call will be different

## When Not To Use It

If default is not always necessary, you may disable this rule.
-->

## 延伸阅读
* [self:: vs className:: inside static className metods in PHP](http://stackoverflow.com/questions/3481085/self-vs-classname-inside-static-classname-metods-in-php)

## 译者

* [cxbig](https://gitub.com/cxbig)
