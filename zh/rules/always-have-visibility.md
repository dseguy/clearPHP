<!-- 好的实践 -->
# 总是定义 类 的 属性 和 方法 的可见度

为了兼容性，PHP允许不定义 **方法** 和 **属性** 的 **可见度** ：`public`，`protected` 或 `private`。  
默认的，**方法** 和 **属性** 会被定义为`public`。可以被其他 **类** 不加限制的访问。

一个开发的方向是将 **可见度** 默认设置为`private`。然后，根据需要进行提权，用于继承访问或外部访问。

这是面向对象编程的一个核心准则：**封装**。尽可能的将 **类** 的内部与外部区隔开来，仅开放少数必要的 **方法** 和 **属性**。

推荐总是设置可见度，尽量加大约束。

## 规则细节

本规则针对 **类** 的 **属性** 和 **方法** 被漏掉的 **可见度** 定义。

如下例子会触发PHP警报：

```php
<?php

abstract class x {
	static $staticProperty;
	var $varProperty;

	function defautVisibilityMethod() {}
	static function defautVisibilityStaticMethod() {}
	final function defautVisibilityFinalMethod() {}
	abstract function defautVisibilityAbstractMethod();

}

?>
```

如下例子是正规的使用方法：

```php
<?php

abstract class x {
	static protected $staticProperty;
	public $varProperty;

	public function defautVisibilityMethod() {}
	static protected function defautVisibilityStaticMethod() {}
	final private function defautVisibilityFinalMethod() {}
	abstract public function defautVisibilityAbstractMethod();
}

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->
