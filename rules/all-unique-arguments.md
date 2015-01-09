<!-- PHP Manual -->
# All Unique Arguments

When defining a PHP method, multiples arguments may carry the same name. 

```php
<?php

function f($a, $a, $a) {
	echo $a;
}

f('b', 'c', 'd'); // prints 'd'

?>
```
The incoming values are assigned to the arguments in the same order than in the method definition : the last one overwrite the first. 

```php
<?php

function f($a, $b, $a) {
	echo $a;
}

f('e', 'f', 'g'); // prints 'fg'

?>
```

It is recommended to always use distinct names for arguments variables.

## Rule Details

The following patterns are considered warnings:

```php
<?php

function f($b, $a, $a) { /**/ }

function f($a, $b, $a) { /**/ }

function f($a, $a, $a) { /**/ }

function f(Stdclass $a, $a) { /**/ }

function f(Stdclass $a, $a = 2) { /**/ }

function f(Stdclass $a, &$a) { /**/ }

?>
```

The following patterns are not considered warnings:

```php
<?php

function f($a, $b, $c) { /**/ }

?>
```
<!--
### Options
-->
## When Not To Use It
Always use this.

<!--
## Further Readings
-->
