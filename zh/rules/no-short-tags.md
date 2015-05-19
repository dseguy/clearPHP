<!-- PHP Manual -->
# 不使用PHP短标记

“PHP允许使用短标记 `<?`   （不鼓励使用。只有`php.ini`中的选项`short_open_tag`被开启时有效，或是在命令行中加上 `--enable-short-tags` 选项）。”

## 规则细节

本规则要求 __不要使用__ 短标记作为PHP代码段的起始。如下例子将会触发 `E_WARNING`：

```php
<?
// ... some code
?>
```

如下代码例子为正规的使用方式：

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
