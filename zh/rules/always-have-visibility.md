<!-- 最佳实践 -->
# 永远都有可见性

为了兼容性的原因，PHP允许方法和属性被定义为没有可见性的: ‘公有’，‘保护'或'私有'。缺省情况下，方法和属性被定义为'公有'，使它们对所有其他的对象可见没有任何限制。

一个开放的途径是把可见性开始都设置为‘私有’，然后，随着资源有被父类或其他外部对象使用的需要，移除必要的限制。

这是一个面向对象编程的一个核心原则：封装。它必须被使用以来把对象内部实现和外部分离，限制冲击仅仅对于选择的方法和属性。

总是使用可见性是被推荐的，越严厉越好。

## 规则详情

这个规则目的是避免省去了方法和属性的可见性。

下面的模式是将被视为警告：

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

下面的模式将不会被视为警告：

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
### 选择

## 什么时候不用它

## 进一步阅读
-->

