<!-- PHP Manual -->
# Always Compare With ===

Some PHP functions use `false` as return value when they fail to run the requested instruction. Simultaneously, they also may return a value that is mistakable with false. The most famous function is `strpos` : 

```php
<?php

$string = "abcde";

if (strpos($string, "a")) { 
	print "Found a\n";
}


if (strpos($string, "b")) { 
	print "Found b\n";
}

?>
```

This example will find 'b' but not 'a'. This is because 'a' is found at the first position in the string, which means an index of 0. Since PHP turn this 0 into false, the first condition fail and 'a' is not found. 

The solution here is to compare the value and the type of the returning value, using the `===` or `!==` operators : they first compare the type of the value, then the value itself. 

```php
<?php

$string = "abcde";

if (strpos($string, "a") !== false) { 
	print "Found a\n";
}


if (strpos($string, "b") !== false) { 
	print "Found b\n";
}

?>
```
This behavior is shared by the following list of PHP functions : 

* array\_search
* collator\_compare
* collator\_get\_sort\_key
* current
* fgetc
* file\_get\_contents
* file-put-contents
* fread
* iconv-strpos
* iconv-strrpos
* imagecolorallocate
* imagecolorallocatealpha
* mb-strlen
* next
* pcntl\_getpriority
* preg\_match
* prev
* readdir
* stripos
* stristr
* strpos
* strripos
* strrpos
* strstr
* strtok
* PDO::exec
* SplFileObject::fgetc
* ext/event::search
* ext/event::searcheol

It is recommended to always use `===` or `!==` operators, even when the context suggest the returned value is not 0.

## Rule Details

Using any of the above PHP methods in the context below is considered a warning:

```php
<?php

if (strpos($haystack, $needle)) {
	/* doSomething() */
}

while (next($array)) {
	/* doSomething() */
}

do {
	/* doSomething() */
} while (current($array));

?>
```

The following patterns are not considered warnings:

```php
<?php

// This is explicitely checking for unfound needle
if (strripos($haystack, $needle) === false) {
	/* doSomething() */
}

// This is explicitely checking for found needle at offset 0
if (strtok($haystack, $needle) === 0 ) {
	/* doSomething() */
}

?>
```
<!--

### Options
-->

## When Not To Use It
Always use this.

## Further Readings
* [Comparison operators](http://php.net/manual/en/language.operators.comparison.php)
* [Booleans](http://php.net/manual/en/language.types.boolean.php)
