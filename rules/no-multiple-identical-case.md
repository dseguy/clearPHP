<!-- Good Practices -->
# No Multiple Identical Case

`switch` instructions doesn't handle multiple identical cases. In fact, it does handle them by using the first and never using the later.

```php
<?php

switch ($x) {
	case 1 :
		$y = 2;
		break; 
	
	case 1 :
		$y = 3;
		break;
	
	default : 

}

?>
```

`switch` scans through the `cases` until it finds one that is true. When this is the case, it runs the related code, and, usually, breaks out of the switch. Multiple identical `cases` are ignored, except the first one. 

Be aware that, given the flexible nature of `case`, it is possible to have multiple identical `case` with different shapes : 

```php
<?php

switch ($x) {
	case 1 :
		$y = 2;
		break; 
	
	case 1 :
		$y = 3;
		break;
	
	default : 

}

?>
```

This is also true for the `default` instruction : PHP compiler will accept several of them in a switch, but will only run the first. 

```php
<?php

switch ($x) {
	case 1 :
		$y = 2;
		break; 
	
	default : 
	   $y = 3;
	   break;

	default : 
	   $y = 4;
	   break;
}

?>
```

It is recommended to make sure that switch instructions are all distinct, and only has one `default` instruction.

## Rule Details

This code is considered a warning : 
```php
<?php

switch ($x) {
	case 1 :
		$y = 2;
		break; 
	
	default : 
	   $y = 3;
	   break;

	default : 
	   $y = 4;
	   break;
}

?>
```

This code is considered valid : 

```php
<?php

switch ($x) {
	case 1 :
		$y = 2;
		break; 
	
	case 2 : 
	   $y = 3;
	   break;

	default : 
	   $y = 4;
	   break;
}

?>
```

## When Not To Use It
You won't believe it when you'll find a violation of this one. 

## Further Reading
* [switch](http://php.net/manual/en/control-structures.switch.php)


