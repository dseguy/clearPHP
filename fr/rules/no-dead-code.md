<!-- Good Practices -->
# No Dead Code

Dead code is code that is not used. There may be two kind of situations : unreachable code and unused code. 

Unreachable code happens when valid instruction is located where PHP will never reach them. This happens if some branching is executed before reaching the code itself. Here are some examples : 

```php
<?php

function y() {
	return $x++; // ++ is unreachable
}

?>
```

Unused code happens when structures are defined but never used. For example, a function may be defined, but is never called. Such function will use coding space, require compilation and may also be included in extra tasks like Unit tests or code review. But if it isn't used, all that is wasted. 

It is recommended to spot as much dead code as possible, and remove it.

## Rule Details

The following patterns are considered warnings:

```php
<?php

if (0) {
	$deadCode++;
}

function y() {
	return $x++; // ++ is unreachable
}

switch ($x) {
	case 1 : 
		$a++;
		break 1;
		$b++; // $b can't be reached
	default : 
		$c++;
		break 1;
	case 2 : // can't be reached 
		$d++;
}

function z() {
	die();
	return 3; // return can't be reached
}

function w() {
	return $a; 
	$a++ // $a++ can't be reached
}


?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

