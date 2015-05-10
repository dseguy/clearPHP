<!-- Good Practices -->
# No Nested Ternary

The ternary operator is a compact version of a `if then else` structure. It is very convenient when the branching is needed but should be inline with the rest of the code.

```php
<?php
print 'Result : '.( $success ? 'transaction succeded' : 'transaction failed');
?>
```
Ternary operators may be nested. This degrades very quickly the readability of the code.

```php
<?php
print 'Result : '.( $success ? $christmas ? 'transaction success and you get a gift' : 'transaction success' : 'transaction failed');
?>
```

It must also be mentioned that ternary may not produce the expected result when nesting them. For example : 

```php
<?php

echo $foo ? 'a' : $bar ? 'b' : 'c';

?>
```

Here is the result for all values of `$foo` and `$bar` : 

| `$foo` | `$bar` | result |
|--------|--------|--------|
| true   | true   | b      | 
| true   | false  | b      | 
| false  | true   | b      | 
| false  | false  | c      | 

It is recommended to avoid nesting ternary operators. 

## Rule Details

Ternary operators are fine. Nesting them hurts. 

The following code will raise a warning : 

```php
<?php

$foo ? 'a' : $bar ? 'b' : 'c';

$foo ?: $bar ? 'b' : 'c';

$foo ?: $bar ?: 'c';

?>
```

The following code will is legit : 

```php
<?php

$a = $bar ? 'b' : 'c';
$d = $foo ? 'a' : $b;

if ($foo) {
	$d = 'a';
} elseif ($bar) {
	$d = 'b';
} else {
	$d = 'c';
}

?>
```

<!--
## When Not To Use It
Never


## Further Reading 
-->
