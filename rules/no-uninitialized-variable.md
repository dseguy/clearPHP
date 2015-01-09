<!-- Performances -->
# No Uninitialized Variables

When calling a method or a function, the arguments passed by reference, and signaled in the signature by `&`, must be one of the following : 
* Variables or arrays : `$v` or `$x[1]`
* New objects : `new stdClass()`
* References

```php
<?php

    $htmlLink = '<a href="'.strtr(strtolower($url), ' ', '-').'.php"><img src="'.strtr(strtolower($url), ' ', '-').'.png" alt="$title"></a>';
?>
```

PHP doesn't check that functioncall are 

```php
<?php

	$baseUri = strtr(strtolower($url), ' ', '-');
    $htmlLink = '<a href="'.$baseUri.'.php"><img src="'.$baseUri.'.png" alt="$title"></a>';

?>
```

This has the added advantage of making the second line easier to read, and to update (as long as both URIs are build the same way). 

When the functioncall is used once, there is no gain to cache it in a variable. As soon at the functioncall is used twice, there is some gain. Of course, the simpler the functioncall and the fewer the reuse, the lesser is the gain. 

It is recommended to avoid recalculation in any function scope. In the global scope, this is also recommended, although it may be harder to spot. 

## Rule Details

This rule is aimed at avoiding recalculating the same values several times.

The following patterns are considered warnings:

```php
<?php

	// $url is calculated twice identically
    $htmlLink = '<a href="'.strtr(strtolower($url), ' ', '-').'.php"><img src="'.strtr(strtolower($url), ' ', '-').'.png" alt="$title"></a>';

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

## Further Readings
-->

