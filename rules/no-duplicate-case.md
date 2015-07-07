<!-- Good Practices -->
# No Duplicate Case In Switch

Disallow the creation of duplicate `case` in `switch` statement. 

Duplicate `case` happens when the same value is used several times as target for case : 

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
```

Duplicate case may also happen when several targets are the same when compared with `==`. Mixing types will lead to confusion as PHP might consider them equals. For example, the following are all duplicate : 

```php
<?php

switch($a) {
	case array(1): 
		break 1;
	case 1:         // double case
		break 1;
	case 'asdf';    // double case
		break 1;
	case 1.0:       // double case
		break 1;
	case true:      // double case
		break 1;
	default:	
}
?>
```

This is useless as the second defined case will be silently ignored.

It is recommended to check that all case values are distinct. It is also recommended to check that case's target are of the same time.

## Rule Details

This rule require that every `switch()` statement has unique literal case, or complex calls. The following patterns are wrong. 

```php
<?php

// duplicate case
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

// mixing types for target
switch($a) {
	case array(1): 
		break 1;
	case 1:         // double case
		break 1;
	case 'asdf';    // double case
		break 1;
	case 1.0:       // double case
		break 1;
	case true:      // double case
		break 1;
	default:	
}
?>
```

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