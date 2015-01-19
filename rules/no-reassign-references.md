<!-- PHP Manual -->
# No Reassign References

"References in PHP are a means to access the same variable content by different names." There is a separation between the variables names and their related content : this way, several distinct variables may refer to the same content. Changing one content will change the content for the others.

```php
<?php

$a = 'a';
$b = &$a;
$b .= 'b';

print $a; // displays ab

?>
```

On the other hand, this example, adapted from the PHP manual, will not work as expected. 

```php
<?php

function foo(&$b)
{
    $b =& 'b';
}

$a = 'a';
foo($a); 

print $a; // display a, not b
?>
```

Here, a reference is indeed created at functioncall time. `$b` is a reference to the same content than the original variable `$a`. However, assigning a new reference to `$b` will only change the reference in `$b` : it will not change the content of `$b`. This way, the new reference is lost, and `$a` stays unchanged.

The following would work as expected : 

```php
<?php

function foo(&$b)
{
    $b = 'b';
}

$a = 'a';
foo($a); 

print $a; // display b
?>
```

It is recommended to avoid reassigning references in a function's argument, and only change their content. 

## Rule Details

The following patterns are considered warnings:

```php
<?php

function foo(&$b)
{
   $c = 'c';
   $b = &$c;
}

?>
```

The following patterns are not considered warnings:

```php
<?php

function foo(&$b)
{
   $c = 'c';
   $b = $c;
}

function bar(&$b)
{
   $c = $b.'c'; // although the reference on $b is useless
   return &$c;
}

?>
```

<!--
### Options
-->
## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically. 

<!--
## Further Readings
-->

