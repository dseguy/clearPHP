<!-- 性能 -->
# 不保留调试代码

调试代码有如下风格：
* `var_dump` 和 `print_r`
* `print` 或 `echo` 带上信息（例如 `echo 'DEBUG';`。带有HTML的注释或 `$debug` 信息。
* 辅助方程或类，如 `Kint`、 `php-ref`、 `dump_r`、 `Krumo`、 `dBug`。

```php
<?php

if (!is_object($dbconnexion)) {
	debug($dbconnexion);
	die();
}

?>
```

强烈建议在生产环境中移除所有调试代码，以避免被意外调用（生产环境中可能泄露敏感信息）。

## 规则细节

以下例子将认为是一个警告：

```php
<?php

print 'debug';

require '/kint/Kint.class.php';
Kint::dump( $_SERVER );

?>
```
<!--

### Options

## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically.

## Further Readings
-->

## 译者

* [cxbig](https://github.com/cxbig)
