<!-- Good Practices -->
# One Instruction Per Line

Several instructions on the same line makes it hard to read, and easy to miss some special situations. We are accustomed to see a new instruction every line. 

```php
<?php

$a1 = 2; $b2 = 3; $c = 2;

array_map($anArray, function($x) { $x = subtr($x, 0, 5); $x .= '00.3'; return $x + 2; ) 

?>
```

Several identical instructions on the same line makes all of them indistinct. And when the instructions are distinct, it create a confusing line of code. 

It is recommended to check each line has one instruction at most. 

## Rule Details

The following are considered a warning : 

```php
<?php

$a1 = 2; $b2 = 3; $c = 2;

array_map($anArray, function($x) { $x = subtr($x, 0, 5); $x .= '00.3'; return $x + 2; ) 

?>
```

The following pattern is considered OK :

```php
<?php

for($i = 0; $i < 10; $i++) 
{ /**/ }
?>
```
<!--
### Options

## When Not To Use It

If default is not always necessary, you may disable this rule.


## Further Reading
* []()
-->