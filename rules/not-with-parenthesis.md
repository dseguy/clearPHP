<!-- PHP Manual -->
# Not With Parenthesis

Language constructs are a special set of PHP functions. They look the same from a user point of view, but are processed different under the hood. Even all of them do not behave the same, 

Here, we are considering the following : `echo`, `print`, `die`, `exit`, `return`, `include`, `include_once`, `require` and `require_once`.

Those one, among other differences with normal functions, they do not require parenthesis, while functions, native or custom, do need them. 

```php
<?php

function display($message) {
	// unneeded parenthesis
	echo $message; 
}

// needed parenthesis
display('My message');

?>
```

PHP manual is explicit for `return`'s usage of parenthesis : "You should never use parentheses around your return variable when returning by reference, as this will not work. You can only return variables by reference, not the result of a statement. If you use return ($a); then you're not returning a variable, but the result of the expression ($a) (which is, of course, the value of $a)."

It is possible to call language constructs with parenthesis. This is a nice trick : PHP will apply parenthesis to the argument, and that will make an expression. The expression is evaluated, and since the parenthesis represents identity (they don't change the result of the expression), it seems that with or without parenthesis is OK. 

```php
<?php

echo('a');
echo 'a';

// if echo was a function, the above is equivalent to : 
echo( ('a') );
echo(  'a'  );

?>
```

There are two consequences to this : first, if a variable is used as argument, especially a reference, then the reference is lost. Expression do no preserve the reference, at it needs to combine values. 

```php
<?php

function &foo() {
	$x = 3;
	$y = &$x;
	
	return (&$y);
}

?>
```

The code above will build the reference in `$y`, but at the last moment, evaluate the expression `(&$y)` and return a value. Not using parenthesis is a good way to keep that principle visible. 

The second source of bugs is that the parenthesis will not link the arguments to the calling function, or language construct. For example, this code : 

```php
<?php

require('path/to/file.txt') or die('library not found');

// what it is really : 
require( ('path/to/file.txt') or die());

?>
```
Here, the logical `or` is used with higher priority. It will then turn the whole expression into 1, since the string is always true. This is confusing. 

It is recommended to never use parenthesis with the language constructs.


## Rule Details

The following are the different language constructs : 

* return
* exit
* die
* require
* require_once
* include
* include_once
* echo
* print

Note that the following language constructs will require parenthesis : 

* unset
* isset
* empty

The following code is considered a warning:

```php
<?php

function x() {
	return ($a);
}

print($x);
echo ($z);

?>
```

The following pattern is considered legit:

```php
<?php

function x() {
	return $a;
}

print $x;
echo $z;


?>
```

<!--
## When Not To Use It
-->

## Further Reading 

* [Return] (http://php.net/manual/en/function.return.php)
