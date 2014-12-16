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
* Security wise, `eval` will most probably be fed with data that are not known at coding time, may be even with input from the internet user. Such code has to be systematically sanitized before it is used. 

It is highly recommended to avoid using `eval` function and rely on other dynamical features of PHP such as variables variables. 


## Rule Details

Any usage of `eval`  is forbidden. 

```php
<?php

	if(substr($variable, 0, 9) === '$GLOBALS[')){
		eval("\$value =\"$format[sql]\";");
	}

?>
```

## When Not To Use It
Please, always use this

## Further Reading
* [Using Eval in PHP](http://blog.joshuaeichorn.com/archives/2005/08/01/using-eval-in-php/)
* [Eval](http://php.net/manual/en/function.eval.php)