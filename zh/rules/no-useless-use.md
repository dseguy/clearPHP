<!-- 好的实践 -->
# 不要无效的Use

在命名空间开头使用 `use` 申明可以让PHP在整个类定义中找到对应的类。PHP会收集和使用找到的类，在当前文件的实际使用中正确的调用。

任何多余的 `use` 申明都会额外消耗资源去寻找对应的类，包括处理不必要的命名冲突。

```php
<?php

namespace name {
	// foobar 是无用的
	use foo, bar, foobar;

	class barfoo extends foo implements bar {

	}
}

?>
```

建议保留最小需求的 `use`。

## 规则细节

如下代码被视为警告：

```php
<?php

namespace name {
	// foobar 是无用的
	use foo, bar, foobar;

	class barfoo extends foo implements bar {

	}
}

?>
```

<!--
### Options

## When Not To Use It
-->

## 译者

* [cxbig](https://github.com/cxbig)
