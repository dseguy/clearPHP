<!-- PHP Manual -->
# No Return With Parenthesis

From the PHP manual : "You should never use parentheses around your return variable when returning by reference, as this will not work. You can only return variables by reference, not the result of a statement. If you use return ($a); then you're not returning a variable, but the result of the expression ($a) (which is, of course, the value of $a)."

It is possible to call `return` with parenthesis, but PHP manual does recommend not to use them. 

```php
<?php

function x() {
	return ($a);
}

?>
```
`return` is not a real function, but a language construct, which makes parenthesis optional. Since this is less coding and less processing, it is recommended to never use them.

This will also prevent bugs when function return by reference : if there are parenthesis around the returned value, then a reference on the expression will be returned, and will be useless. 
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
