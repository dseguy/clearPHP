<!-- PHP Manual -->
# No Return With Parenthesis

From the PHP manual : "You should never use parentheses around your return variable when returning by reference, as this will not work. You can only return variables by reference, not the result of a statement. If you use return ($a); then you're not returning a variable, but the result of the expression ($a) (which is, of course, the value of $a)."

It is recommended to never use parenthesis in a return statement.


## Rule Details

The following code is considered a warning:

```php
<?php

function x() {
	return ($a);
}

?>
```

The following pattern is considered legit:

```php
<?php

function x() {
	return $a;
}

?>
```

<!--
## When Not To Use It

-->

## Further Reading 

* [Return] (http://php.net/manual/en/function.return.php)
