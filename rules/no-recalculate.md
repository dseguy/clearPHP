<!-- Performances -->
# No Recalculate

Within a scope, it is always faster to cache any calculated value than recalculate it. For example, 

```php
<?php

    $htmlLink = '<a href="'.strtr(strtolower($url), ' ', '-').'.php"><img src="'.strtr(strtolower($url), ' ', '-').'.png" alt="$title"></a>';
?>
```

In this example, both the URI link and the image URI are built from the `$title` variable, with some characters replacements. Calling both `strtr` and `strtolower`, or even one of them only, will be slower than calling them once, and caching the result in a variable. 

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
The following patterns are not considered warnings:

```php
<?php

	// URI are distinct
    $htmlLink = '<a href="'.strtr(strtolower($url), ' ', '-').'.php"><img src="'.strtr(strtolower($url.'?id='.time()), ' ', '-').'.png" alt="$title"></a>';
    
    // les appels de la fonction sont différents
    $a = foo(1);
    $b = foo(2);
?>
```
<!--

### Options
-->

## When Not To Use It
* Avoid creating variables to hold some value in the global context, as it may be difficult to spot the reuse across the whole application. It is safer within a method.
* Some functioncalls not only return a result, but also change the state of the called system, such as  `ini_set` or a status method. With such methods, the result may be cached, but the call is still necessary.

<!--
## Further Readings
-->

