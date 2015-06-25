<!-- Good Practices -->
# 注释所有条件穿透

`case` 在 `switch` 结构中通常以 `break` 关键字结束。

它们也可以“掉落”到下一个 `case` 条件中继续运行，只要不定义 `break` 就可以。
这种方法可以将多个 `case` 合并到一起处理。这叫做“条件穿透”。

条件穿透通常很少用到。当此用法出现时，通常都是直接穿透多个条件，使用同样的处理方式。

使用条件穿透是没有问题的。但是，最好注释一下，算是强调它的用途。

## 规则细节

本规则要求每个不带 `break` 关键字的 `case` 都带上一个注释。  
如下例子将视为一个警告：

```php
<?php
// case 'b' 是没有注释的条件穿透
switch (foo) {
    case 'a':
    case 'c':
        doSomethingForA();
        // will also do for c
        break 1;

    case 'b':
        doSomethingForB();

    default:
        doSomethingForDefault();
}
?>
```

以下例子视为正规的方法：


```php
<?php
// 所有条件穿透都带有注释
switch (foo) {
    case 'a':
    case 'c':
        doSomethingForA();
        // will also do for c
        break 1;

    case 'b':
        doSomethingForB();
        //also apply default behavior

    default:
        doSomethingForDefault();
}
?>
```
<!--
### Options

## When Not To Use It

If default is not always necessary, you may disable this rule.
-->

## 译者

* [cxbig](https://github.com/cxbig)
