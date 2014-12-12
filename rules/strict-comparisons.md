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

The solution is to use `===`, 


## Rule Details

This rule targets code that doesn't do anything useful. 

The following code is considered a warning:

```php
<?php
// literals in the code flow
1; 
My_CONSTANT;
$b;
function () { return $x = 3; }

// post-incrementation in a return
return $a++;

?>
```


The following pattern is considered legit:

```php
<?php
// properties may be processed with __get()
$object->property;

// pre-incrementation in a return
return ++$a;
?>
```

<!--
## When Not To Use It

-->

## Further Reading
*[Strict vs. Loose Comparisons in PHP](http://www.copterlabs.com/blog/strict-vs-loose-comparisons-in-php/)