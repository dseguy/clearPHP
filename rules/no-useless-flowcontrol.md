<!-- Good Practices -->
# Useless Flow Control

Useless flow control are valid flow control that have no impact on the code. 


```php
<?php
   if ($a == 1);
        print("Hello, world");

   if ($b == true) {
		// process this special case
	}

?>
```
Useless flow control are often the result of a typo, like the first case above : the extra semi-colon should be removed. Or, it may be forgotten situations that need more writing. 

They should be removed or completed so as to have an actual impact in the code.

## Rule Details

This rule targets flow control instruction that doesn't do anything useful. 

The following code is considered a warning:

```php
<?php
   if ($a == 1);
        print("Hello, world");

   if ($b == true) {
		// process this special case
	}
	
	for($i = 1; $i < 10000; $i++) {
		
	}
?>
```


The following pattern is considered legit:

```php
<?php

switch($x) {
	case 'a':  // no action upon 'a'
		break; 
		
	case 'b': 
		$a++;
		break;
	
	default: 
		break; 
}

?>
```

<!--
## When Not To Use It



## Further Reading

-->