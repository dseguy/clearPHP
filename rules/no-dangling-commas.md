<!-- Good Practices -->
# No Dangling Commas

In PHP, one may leave one empty slot at the end of an array definition. The last empty slot will simply be ignored at compile time, and will not generate an empty value.

```php
<?php
$array = array('a', 
				  'b',
				 );
$array2 = ['c', 
			 'd',
			];
?>
```

This is valid syntax, and may be convenient if you plan to add other values in those arrays in the future. 

This is also quite strange for developpers used to other languages. 

## Rule Details

This rule targets array definitions that have an empty last slot. 

The following code is considered a warning:

```php
<?php
$array = array('a', 
				  'b',
				 );

$array2 = ['c', 'd', ];
?>
```


The following pattern is considered legit:

```php
<?php
$array = array('a', 
				  'b'
				 );

$array2 = ['c', 'd', ];
?>
```

## When Not To Use It
If you are juggling with multiple technologies, or use other technologies that are stricter with arrays, it is a good idea to apply it too. 

## Further Reading

* [arrays in PHP](http://php.net/manual/en/function.array.php)