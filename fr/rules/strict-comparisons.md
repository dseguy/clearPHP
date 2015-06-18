<!-- Good Practices -->
# Strict Comparisons

PHP makes a effort at simplifying the programmer's life by automatically casting the values in a comparison to a comparable type. 

```php
<?php
$x = 0;
if ($x == false) { /* doSomething */ }
?>
```

Here, equaling `0` to `false` seems quite natural. Under the hood, PHP does turn the integer `0` to the equivalent as a boolean, which is `false`. The comparison then succeeds. 

```php
<?php
$x = strpos('abc', 'a');
if ($x == false) { /* process error */ } else { /* process finding */}
?>
```
Things gets a little more confusing when some information is carried by the type of the value. Here, `strpos` will return `false` if it can't find the needle (`'a'`) in the haystack (`'abc'`). But it will also return `0` if it finds the needle in the first position, which is indexed with 0. 

The recommendation is to use `===` or `!==` when there are no good reason to use `==` or `!=`. Always compare the returned value to `false` or `true` explicitly.

## Rule Details

This rule targets methods that doesn't compare the result with `===` or `!==` to  `false` or `true`.

Here is a list of PHP native functions that require strict comparison : 

* array\_search
* collator\_compare
* collator\_get\_sort\_key
* current
* fgetc
* file\_get\_contents
* file\_put\_contents
* iconv\_strpos
* iconv\_strrpos
* imagecolorallocate
* imagecolorallocatealpha
* mb\_strlen
* next
* pcntl\_getpriority
* preg\_match
* preg\_match\_all
* prev
* readdir
* stripos
* strpos
* strripos
* strrpos
* strtok

The following code is considered a warning:

```php
<?php

// implicit comparisons
if (strpos('abc', 'a')) {}

// weak comparisons
if (stripos('abc', 'a') == false) {}
if (strrpos('abc', 'a') == 2) {}

// weak and implicit comparisons
if ($res = preg_match('/abc/', $a)) {}

?>
```

The following pattern are considered legit:

```php
<?php

// explicit comparisons
if (strpos('abc', 'a') === false) {}
if (strripos('abc', 'a') !== true) {}

// explicit comparison and assignation
if (($res = readdir('.')) === false) {}

?>
```

<!--
## When Not To Use It

-->

## Bibliographie
*[Strict vs. Loose Comparisons in PHP](http://www.copterlabs.com/blog/strict-vs-loose-comparisons-in-php/)