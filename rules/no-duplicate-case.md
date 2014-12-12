<!-- Good Practices -->
# No Duplicate Case In Switch

Disallow the creation of duplicate `case` in `switch` statement. 

This is useless as the second defined case will be silentely ignored.

## Rule Details

This rule require that every `switch()` statement has unique literal case, or complex calls. The followings are wrong. 

```php
<?php
switch($a) {
	case 1: 
		break 1;
	case 2: 
		break 1;
	case 3: 
		break 1;
	case 1:      // double case
		break 1;
	default:	
}
?>
```php

The following patterns are considered OK :

```php
<?php
switch($a) {
	case $a + 1 == 2:  // complex comparison. Should be reviewed
		break 1;
	case 3: 
		break 1;
	case 1: 
		break 1;
	default:	
}

// normal switch
switch($a) {
	case 2:
	case 3:     // fall through
		break 1;
	case 1: 
		break 1;
	default:	
}
?>
```
<!--
### Options

## When Not To Use It

If default is not always necessary, you may disable this rule.
-->