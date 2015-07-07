<!-- Security -->
# No Eval

`eval` is a PHP function that takes a snippet of code as parameter and will run it, as part of the current code. 

```php
<?php

$php = 'echo "Hello world";';
eval($php);
// Displays Hello world

?>
```

`eval` has two main drawbacks : 

* it is very slow, as PHP as to stop the current processing, compile the code and include it in the current tree, then resume execution. It is also known that opcode caches doesn't cache any `eval`-ed string, and force the recompilation of that code every time. 
* Security wise, `eval` will most probably be fed with data that are not known at coding time, may be even with input from the internet user. If the `eval`'ed code has to include user data, it would need a systematic sanitization that is not possible to do. 

`create_function` is the old style for creating anonymous functions in PHP. It actually relies on the same mechanism than `eval` and should be treated as such. It should be replaced by closures.

It is highly recommended to avoid using `eval` function and rely on other dynamical features of PHP such as variables variables. 


## Rule Details

Any usage of `eval`  is forbidden. 

The following are considered warning : 
```php
<?php

	if(substr($variable, 0, 9) === '$GLOBALS[')){
		eval("\$value =\"$format[sql]\";");
	}
	
	$newfunc = create_function('$a,$b', 'return "ln($a) + ln($b) = " . log($a * $b);');

?>
```

The following are considered legit : 

```php
<?php

	$closure = function ($a , $b) { 
		return "ln($a) + ln($b) = " . log($a * $b)
	};

?>
```

## When Not To Use It
Please, always use this rule.

## Further Reading
* [Using Eval in PHP](http://blog.joshuaeichorn.com/archives/2005/08/01/using-eval-in-php/)
* [eval](http://php.net/eval)
* [create_function](http://php.net/create_function)
* [Closures](http://php.net/class.closure)
