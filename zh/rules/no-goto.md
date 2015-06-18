<!-- 优良实践 -->
# 没有Goto

`Goto` 被考虑为是一个过去时代的事情：它将使代码非常难读和难懂。它导致所有的代码都堆成一团，"意大利面条式"的代码(code spaghetti)和维护头痛。

## 规则详情

下面的代码被考虑为一个警告：

```php
<?php

meaningfulLabel:
if ($x === 2) {
    goto error;
}
if ($y === 3) {
    goto secondError;
}
normal:
print "x, y and z were tested";
return;

error:
print "x is 1!\n";
return;

secondError:
if ($z === 4) {
	goto normal;
}
print "y is 3!\n";
return;

?>
```

<!--
## 啥时候不用它


-->
## 进一步阅读 

* [理性的编程：为什么got是坏的东西？](http://www.drdobbs.com/jvm/programming-with-reason-why-is-goto-bad/228200966)
* [xkcd Goto 漫画](http://xkcd.com/292/)
* [Goto 应被视为有危害](http://c2.com/cgi/wiki?GotoConsideredHarmful)

