<!-- Good Practices -->
# No Duplicate Keys In Array

Disallow the creation of duplicate keys in literal arrays. 

This is useless as the second defined key will overwritte the first silently. 

## Rule Details

This rule require that every `array()` call has unique keys. The following is wrong. 

```php
$a = array(1 => 'a',
			 2 => 'b',
			 3 => 'c',
			 1 => 'a' // double definition
			 );
```php

The following patterns are considered OK :

```php
$a = array(1 => 'a',
			 2 => 'b',
			 3 => 'c',
			 );

$a[1] = 'a'; // this doesn't belong to the literal definition anymore

```
<!--
### Options

## When Not To Use It

If default is not always necessary, you may disable this rule.
-->