<!-- PHP Manual -->
# No Parenthesis For Language Construct

`print` may be called without parenthesis : it, along with a small group of other PHP native structures, are called 'language construct' and are not usual functions. The language constructs are `echo`, `print`, `unset`, `isset`, `empty`, `include`, `include_once`, `require` and `require_once`.


```php
<?php
	print "a\n";
	print("b\n");
?>
```

Although both instructions behave the same, calling `print` with parenthesis has not the same meaning than in a function. Actually, PHP really understands the parenthesis as (sic) parenthesis, and not as arguments delimiters. 

It is easier to understand the situation with the following script : 

```php
<?php

print("a") && print("b");

?>
```

If `print` was a function, then it would display `a` and then `b`. However, the script displays `b1`. In fact, the above script is equivalent to the one below : 

```php
<?php

print( ("a") && print("b")  );

?>
```

The first print function displays the result of `("a") && print "b"`. This expression displays `"b"`, then return `1`, and  `("a") && 1` is processed, resulting in 1. At that point, the second `print` is actually run. 

It is recommended not to use any parenthesis with language constructs, so as to avoid such pitfall.

## Rule Details

The following pattern is considered warnings:

```php
<?php

print("a") && die()  );

?>
```

The following pattern are considered legit:

```php
<?php

	// tolerated
	// print is alone in the expression
	print ("b");

	// better
	include "c";
	echo "b";
?>
```
<!--
### Options
-->

## When Not To Use It

If `print` is always used alone in the expression, there is no need to chase them all. 

## Further Reading 

* [Variable functions](http://php.net/manual/en/functions.variable-functions.php)
* [print](http://php.net/print)