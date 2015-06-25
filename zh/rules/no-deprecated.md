<!-- PHP 手册 -->
# 不要使用 被遗弃(deprecated) 的特性

在不断的版本更替中，PHP会遗弃一些特性。它们会被新的特性替代，或不再使用。这在一个平台的发展中，是很常见的现象。被遗弃的特性在一段时间内会先被标记为 `deprecated`。然后从后续版本中移除。

举个例子，组件 `ext/mysql` 在 `PHP 5.5` 版本中被彻底移除。它在此之前的若干版本中已被标记为 `deprecated`。在当前的 `PHP 5.6` 版本中，`$HTTP_RAW_POST_DATA`、PHP的配置条目 `iconv.input_encoding` 和其相关条目、还有一些静态访问的方法已经被标记为 `deprecated`。它们也将在后续版本中被彻底移除。

## 规则细节

本规则针对被标记为 `deprecated` 的或已经被移除的代码。  
在PHP手册中，你可以很容易的找到每个版本的 `deprecated` 列表。

## 什么时候不用此规则

如果你计划将你的应用程序和某一个PHP版本捆绑起来，那么你可以安全的忽略本规则。

## 延伸阅读

* [在 PHP 5.6.x 中被标记为 **deprecated** 的特性](http://php.net/manual/zh/migration56.deprecated.php)
* [在 PHP 5.5.x 中被标记为 **deprecated** 的特性](http://php.net/manual/zh/migration55.deprecated.php)
* [在 PHP 5.4.x 中被标记为 **deprecated** 的特性](http://php.net/manual/zh/migration54.deprecated.php)
* [在 PHP 5.3.x 中被标记为 **deprecated** 的特性](http://php.net/manual/zh/migration53.deprecated.php)

## 译者

*  [cxbig](https://github.com/cxbig)
