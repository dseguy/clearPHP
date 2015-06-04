<!-- 优良实践 -->
# 关键字（应该）小写

通常来说PHP关键字应该用小写。大写是可能的，但是看上去很丑而且从来没有听说过有人这样干。

```php
<?php
IF (OK_FOR_CONSTANTS) {
	PRINT "Result : ";
} ELSE {
	ECHO "Result : ";
}
?>
```

## 规则详情

所有的PHP关键字都应该小写，除了常量`TRUE`, `FALSE`,`NULL`，它们的大写可以忍受。另外还有PHP的常量，它们一般总是被写成大写。

这是不对的: 

```
<?php
DO {
	print "Result : ";
} While ($x AnD $y === FALSE);
?>
```

这是对的: 

```php
<?php
do {
	print "Result : ";
} while ($x and $y === FALSE);
?>
```


<!--
## 什么时候不要用它
永远


## 进一步阅读 
-->
