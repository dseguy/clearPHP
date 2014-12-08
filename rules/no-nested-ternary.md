<!-- Good Practices -->
# No Nested Ternary

The ternary operator is a compact version of a `if then else` structure. It is very convenient when the branching is needed but should be inline with the rest of the code.

```php

print "Result : ".( $success ? 'transaction succeded' : 'transaction failed');

```
Ternary operators may be nested. This degrades very rapidely the readability of the code.

```php

print "Result : ".( $success ? $christmas ? 'transaction success and you get a gift' : 'transaction success' : 'transaction failed');

```

## Rule Details

Ternary operators are OK. Nesting them hurts. 

<!--
## When Not To Use It
Never


## Further Reading 
-->
