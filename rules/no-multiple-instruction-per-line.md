<!-- Good Practices -->
# No Multiple Instruction Per Line

PHP uses the semicolon `;` for instruction separation. New expressions starts on a new line, making it easier to spot.

```php
<?php

class x {
	const a = 1;
	const b = 2;
	const c = 3;
}

?>
```
PHP also allows merging several operations in one, when they share some common meaning or operator.

```php
<?php

class x {
	const a = 1, b = 2, c = 3;
}

?>
```

However, lining several instructions on the same line will break the readability of the code, and make it harder to spot special situations. 

```php
<?php

switch ($x) {
	case 'a' : $a = 1; break 1;
	case 'b' : $a = 2; // fall throw
	case 'c' : $a = 3; break 1;
	case 'd' : 
		$a = 4; 
		$b = 5; break 1; 
	default : 
}

?>
```

It is recommended to make sure one instruction on one line, or use the merged version of the instruction. 

## Rule Details

This code is considered a warning : 
```php
<?php

$a = 'a'; $a .= 'bc'; $a .= 'c';


if ($a == 0) {if ($b) {$c ^= $d; $e ^= $f;} else {$g = $h; $i = $j; $k = $l; $m = $n;}}

?>
```

This code is considered valid : 

```php
<?php

class x {
	const a = 1;
	const b = 2;
	const c = 3;
}

class x {
	const a = 1, b = 2, c = 3;
}

?>
```

```php
<?php

$a = 'a';
$a .= $bc;
$a .= 'c';

// or

$a = 'a' . $bc . 'c';

?>
```

```php
<?php

    if ($a == 0) {
    	if ($b) {
    		$c ^= $d; 
    		$e ^= $f;
    	} else {
    		$g = $h; 
		    $i = $j; 
		    $k = $l; 
		    $m = $n;
		}
	}

?>
```


<!--
## When Not To Use It
Please, always use this

## Further Reading
* 

-->
