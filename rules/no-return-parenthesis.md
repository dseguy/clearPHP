<!-- PHP Manual -->
# No Parenthesis For Return

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
 

## Rule Details

This is considered a warning : 

```php
<?php

function x() {
	return ($a);
}

?>
```

This is considered legit code : 

```php
<?php

function x() {
	return ($a);
}

?>
```

<!--
## When Not To Use It
Please, always use it.
-->

## Further Reading

* [Return](http://php.net/manual/en/function.return.php)