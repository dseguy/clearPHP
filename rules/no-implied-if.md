<!-- Good Practices -->
# No Implied If

PHP has `if...then` structures to handle conditional situations. 

It also has herited from C behavior : in a `or` expression, the right expression will not be executed if the left expression is right. Indeed, since one of the expression only is needed to be true for the couple to succeed, the second expression has no need to be evaluated, saving some processing. 

```php
<?php

$link = mysql_connect('host', 'user', 'pass') || die();

?>
```

The above code is the same as the one below : 

```php
<?php

if (!($link = mysql_connect('host', 'user', 'pass')) { 
	die();
}

?>
```
The same kind of `if..then` structure may be build with `and` though they are less popular. They also work with `and`, `||` and `&&`. 

This is an 'implied if' : the logical operator is made to combine logically two expressions, while it is used here to recreate a `if..then` structure. 

Another alternative is to use the ternary operator, that may be more suitable to certains situations (like concatenation) than `if...then`. 

It is recommended to use an explicit `if..then` expression when the code is intented to embody a condition, and let logical operator only work within logical expressions. 

## Rule Details

This is considered a warning : 

```php
<?php

// used to ensure some file is already included
!defined('INITED_APP') && include('init_app.php');

// checks for resource
mysql_connect('host', 'user', 'pass') || die('Error with the database');

?>
```

The following are considered legit : 

```php
<?php

// used to ensure some file is already included
if (!defined('INITED_APP')) {
	include('init_app.php');
}

// checks for resource
if (!mysql_connect('host', 'user', 'pass')) {
	// process the situation without die or exit
}

?>
```

<!--
## When Not To Use It
Please, always use it.

## Further Reading

* [Return](http://php.net/manual/en/function.return.php)
 -->
