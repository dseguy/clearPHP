<!-- Good Practices -->
# No Unused Arguments

Arguments are compulsory when calling a method or a function. As such, arguments should be taken into account by the methods, and used, rather than just ignored. 

```php
<?php

function init($uri, $login, $pass) {
	$this->log = new Mysqli($uri, $user, $pass);
}

?>
```

There is a situation where arguments are both unused and necessary : when overloading a method in a class hierarchy. The abstract class may have defined a list of arguments, that are actually unnecessary to the child class, but compulsory because of the abstract parent class. In that situation, argument will not be used. 

```php
<?php

abstract class log {
	abstract function init($uri, $login, $pass);
	// save to some database on $host
}

class logSqlite extends log {
	function init($uri, $login, $pass) {
		// unused arguments linked to abstraction
		$this->log = new SQLite3($uri);	}
}

class logMysql extends log {
	function init($uri, $login, $pass) {
		$this->log = new Mysqli($uri, $user, $pass);	}
}

?>
```

Argument should always be used in a function, even if conditionally.

```php
<?php

// all arguments are used, even if conditionally
function x($a, $b, $c) {
	if ($a > 0) {
		return $b + $c;
	} else {
		return $c;
	}
}

// $b is never used. Giving it a default value doesn't help
function x2($a, $b = 1, $c = 2) {
	if ($a > 0) {
		return 1 + $c;
	} else {
		return $c;
	}
}

?>
```

## Rule Details

The following patterns are considered warnings:

```php
<?php
$x = 10; 
?>
```

By default, unused arguments cause warnings:

```php
<?php
function x ($foo) {
    return 5;
}
?>
```

The following patterns are not considered warnings:

```php
<?php
$x = 10;
$x++;
?>
```

<!--
### Options
-->
## When Not To Use It

If you don't want to be notified about unused variables or function arguments, you can safely turn this rule off.
