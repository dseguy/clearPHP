<!-- PHP Manual -->
# No Buried Assignation 

Assignation is an expression : this makes it possible to do an assignation anywhere an expression may be used. This is very convenient to both test a value and collect it for further processing. 

```php
<?php

if (($id = array_search($haystack, $needle = $arguments)) !== false) {
	// process $id even more
}

?>
```
The condition in the `if` statement will both search for `$needle` in `$haystack`, but it will also assign `$arguments` to `$needle`, and the result of `array_search`to `$id`, while not touching `$haystack`. This shortens the code by two full lines (the two assignations), but it also buries the assignations. They are now difficult to spot in the code, and will surprise anyone reading the code. 

It is recommended to keep assignations as visible as possible.


## Rule Details

This rule is aimed at avoiding direct call to magic methods. The list is the following : 

* \_\_construct()
* \_\_destruct()
* \_\_call()
* \_\_callStatic()
* \_\_get()
* \_\_set()
* \_\_isset()
* \_\_unset()
* \_\_sleep()
* \_\_wakeup()
* \_\_toString()
* \_\_invoke()
* \_\_set_state()
* \_\_clone()
* \_\_debugInfo() 

The following patterns are considered warnings:

```php
<?php

echo $object->__sleep();

// use clone operator directly
$y = $object->__clone();

?>
```

The following patterns are considered legit:


```php
<?php

// within class hierarchy
class x {
	function __toString() { return 'x';}
}

class y extends x {
	function __toString() { return parent::__toString().'y'; }
?>

```
<!--
The following patterns are not considered warnings:

```php
<?php


?>
```


### Options

## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically. 
-->

## Further Readings
*[Magic methods](http://php.net/manual/en/language.oop5.magic.php)
