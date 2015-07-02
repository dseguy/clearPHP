<!-- PHP Manual -->
# No Direct Call To Magic Method 

Magic methods are used by PHP to run custom code at key point of the execution. `__clone` method will be called at cloning time, `__wakeup` when the object is extracted from session storage, or `__set_state ` when the object is processed by `var_export`. 

Outside their intended usage and a relay within the class hierarchy, there is no need to call those methods. 

```php
<?php

// Don't do that! 
echo $object->__toString() ."\n";

echo $object. "\n";


// within class hierarchy
class x {
	function __toString() { return 'x';}
}

class y extends x {
	function __toString() { return parent::__toString().'y'; }
?>
```

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
* [Magic methods](http://php.net/language.oop5.magic)
* [PHP: Don’t Call the Destructor Explicitly](http://www.stoimen.com/blog/2011/11/14/php-dont-call-the-destructor-explicitly/)
