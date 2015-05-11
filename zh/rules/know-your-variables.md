<!-- Security -->
# Know Your Variables

In the old age, `register_globals` used to pour all incoming HTTP variables, extracted from the query string into the global variables. This is over, for the best. 

On the other hand, there are still some PHP native functions that are able to create dynamically variables. Applied to externals sources of data, like the query string, they may create interferences in the script. 

## `parse_str`

For example, `parse_str` and the related `mb_parse_str`, are able to parse a query string, and will return the found variables in a variable passed as second parameter. If the second parameter is omitted, the function will pour those variables into the global registry. 

```php
<?php

$queryString = "a=2";

var_dump($a);
// produce NULL and an error

parse_str($queryString);

var_dump($a);
// produce 2

?>
```

It is recommended to always use `parse_str` and `mb_parse_str` with a second argument.

## `extract`

`extract` takes an array with string keys, and turn each of the key into a variable with the same name. 

It is very dangerous to use this function on incoming values, like `$_GET`, `$_POST`, `$_REQUEST`, `$_FILES`, `$_COOKIES`, `$_SERVER`, `$_ENV`. 

The default behavior is set by the second parameter : `EXTR_OVERWRITE` means that `extract` will overwrite existing variables. Not only you will lose the current value, but it will be replaced by another value for which you have no control.

If the variable doesn't exist, extract may pollute the current scope with a lot of variables, some of them may interfere with the current one. 

It is recommended to use `extract` as rarely as possible. Arrays which index are fully under control is the right situation for its usage. Using it with the option `EXTR_OVERWRITE` is highly discouraged.

## Alternatives 
Finally, it is possible to create lots of variables dynamically with the `$$` notation and loops. 

```php
<?php

$variableArray = array('a' => 'b', 'c' => 'd');

foreach($variableArray as $name => $value) {
	$$name = $value;
}

?>
```

This is an alternative to the usage of `extract` and should receive the same recommendations. It should be used rarely, and with arrays whose keys are under control.


## Rule Details

The following are considered a warning : 

```php
<?php

// parse_str : wrong usage
parse_str($queryString);

// alternative parse_str : wrong usage
parse_str($queryString, $var);
extract($vars);


// register_global look alike : DANGER
extract($_POST, EXTR_SKIP);

// old style register_global : DANGER
foreach($_GET as $name => $value) {
	$$name = $value;
}

?>
```

The following pattern is considered OK :

```php
<?php

// parse_str usage
parse_str($queryString, $vars);


// extract usage
function juggle() {
	$args = func_get_args();
	
	$args = array_filter($args, function($k) {
    return in_array($k, array('foo', 'bar'));
}, ARRAY_FILTER_USE_KEY);
	
	// will at most produce $a and $b;
	extract($args);
}


?>
```
<!--
### Options
when static or self call will be different 

## When Not To Use It

If default is not always necessary, you may disable this rule.
-->

## Further Reading
* [parse_str](http://php.net/parse_str)
* [extract](http://php.net/extract)
