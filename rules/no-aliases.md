<!-- PHP Manual -->
# No Aliases

PHP has a good number of aliases functions : the same function may have several names, such as `is_int` which may also be called `is_integer` or `is_long`. Both 
`is_int` and `is_integer` are good. On the other hand, `is_long` is kept for backward compatiblity, and may be removed in a future API cleanup. 

It is recommended to use the master function instead of any alias.


## Rule Details

This rules targets code that use aliases and raise a warning for any function that is not the master, according to the manual. The complete list of aliases is available at in the PHP manual.

The following code is considered a warning:

```php
<?php
if (is_long($value)) { 
	// DoSomething()
}

if (is_integer($value)) { 
	// DoSomething()
}
?>
```


The following pattern is considered legit:

```php
<?php

if (is_int($value)) { 
	// DoSomething()
}

?>
```

<!--
## When Not To Use It

-->

## Further Reading 

* [PHP functions aliases] (http://php.net/manual/en/aliases.php)
