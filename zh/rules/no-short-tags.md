<!-- PHP Manual -->
# 不使用PHP短标记

"PHP also allows for short open tag `<?` (which is discouraged since it is only available if enabled using the short_open_tag php.ini configuration file directive, or if PHP was configured with the --enable-short-tags option)."

## 规则细节

本规则要求 __不要使用__ 短标记作为PHP代码段的起始。如下例子将会触发 `E_WARNING`：

```php
<?
// ... some code
?>
```

如下代码例子为正确的使用方式：

```php
<?php


?>
```

```php
<?= $y
?>
```
<!--
### Options

## When Not To Use It

This is not checked by PHP but will lead to bugs.
-->

## 深入阅读
* [PHP 标记](http://php.net/manual/zh/language.basic-syntax.phptags.php)

## 译者

* [Buck CHEN](https://github.com/cxbig)
