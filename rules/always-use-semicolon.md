<!-- Good Practices -->
# Always Use Semicolon

PHP uses semicolon `;` to make distinction between two sequential instructions. 

```php
<?php

$a = 'a';
echo $a;

?>
```

There are a few situations where semicolon are not required, as another token will be used as instruction ending. For example : 

```php
<?php
	echo 'a' 
?>
```
Here, the `echo 'a'` instruction will be closed automatically by the `?>` PHP closing tag. 

In some situations, the missing `;` will make PHP starts the instruction on one line and finish on the next. 


```php
<?php

$a = f() or 
	// $a = b()      // This line was simply commented out
if ($condition) {}	// now the 'if' is depend on the f() call
	
echo 
print 'b';
// This will display b1

?>
```
`continue` and `break` used to accept no value (that will default to 1) or the result of the next expression (up to PHP 5.4) : 

```php
<?php

for ( $i = 0; $i < 5; ++$i )
{
    if ( $i == 2 )
        continue
    print "$i\n";
    // surprising result
}

?>
```
There are quite some instructions that may overflow to the next line, like all operators, and : 
* all operators (math, comparison, logical...)
* echo
* print
* include and include_once
* require and require_once
* exit

This rules doesn't require the adding of extra semicolon when they are not needed.

```php
<?php

for ( $i = 0; $i < 5; ++$i ) { }; // useless semicolon

class x { }; // useless semicolon

?>
```

It is recommended to make sure that all required semicolon are always set, even if they are not compulsory.

## Rule Details

The following patterns are considered warnings:

```php
<?php
echo $a
?>
<?= 3 ?>
```

The following code is not considered warnings:

```php
<?php
include 
	'/some/file.php';
?>
```

<!--
### Options

## When Not To Use It
-->

## Further Readings
* [Instruction separation](language.basic-syntax.instruction-separation)

