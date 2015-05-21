<!-- 优良实践 -->
# 使用常量

在PHP里面有2种方法创建常量：`const` 和 `define`。

`const` 可以用来创建常量。那些常量会被放置于当前的名字空间中。自从PHP5.6开始，静态的常量表达式是可以被使用的，给常量的创建带来一些灵活性。当没有在一个类中使用时，`const`必须用在顶层的名字空间：没有函数，类，或`if..then`以及任何循环结构。所有的东西都必须在编译时知道。这可能给`const`一个它的主要的优点：它比它的同胞`define`的可读性和速度都要好一点。

在另一方面，`define`, 是经过时间考验的来创建常量的函数。它可以用来在代码里任何地方创建常量，使用或不适用动态的表达式。生成的产量将会在全局的名字空间，或者在引入的常量名字在定义时的名字空间。它可以被定义成大小写非敏感。

`define` 倾向于要比`const`慢，而且不会从opcode缓存中得到多少益处。这个特点在使用大量的常量的情绪中额外明显。

只要可能的时候就使用`const`是非常建议的。 

## 规则详情

下面的代码视为一个警告: 

```php
<?php

define('a', 1);
define('b', 'a' . 'c');
define('c', someClass::constant);

?>
```

下面的代码是OK的: 

```php
<?php

define('l', 3, true);
define('m', $x, true);
define('n', array(1,2,3), true); // before PHP 5.6

?>
```

## 什么时候不要使用
为了向后兼容性的目的，或加载配置信息作为常量的时候，`define`仍然是在使用定义时更加方便一点的选择。对于使用来说，两种语法都是好的。

## Further Reading

* [define() 与 const 的比较(PHP 最佳实践)](https://phpbestpractices.org/#constants)
* [define 与 const (Stackoverflow)](http://stackoverflow.com/questions/2447791/define-vs-const)

