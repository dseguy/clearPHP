<!-- Good Practices -->
# Compatible Typehint
In PHP's functions and methods, arguments may have `typehint`, that forces arguments to be objects, compatible with a class or interface, array or callable. When classes and interfaces are used, objects of the same class or implementing the interface, or any of their child may be accepted. 

When such criteria is not met, the code will emit a catchable error. 

This validation will be done at execution time. This rules aims at avoiding any situation where a method is called with the wrong type of arguments, as much as it may be identified at compile time.

## Rule Details

The following are considered a warning : 

```php
<?php

function x(A $a) { /* some Code */ }

x(new b());

?>
```

The following are OK : 

```php
<?php

function x(A $a) { /* some Code */ }

x(new a());

?>
```

<!--
## When Not To Use It

## Further Reading

* []()

-->