<!-- Good Practices -->
# Use Const

There are two ways to create constants in PHP : `const` and `define`. 

`const` may be used to create constants. Those constants will be placed the current namespace. Since PHP 5.6, static constant expressions may be used, giving some flexibility on constant creation. When not used in a class, `const` must be used at the top level of a namespace : no function, class, nor `if..then`  or any loop structure. All has to be known at compile time. This may give `const` its main advantages : it is slightly faster and more readable than its counterpart, `define`. 

`define`, on the other hand, is the time-honored function to create constants. It may be used to create constants anywhere in the code, with dynamical expressions or not. The resulting constant will be available in the global space, or in the namespace if the namespace was included in the constant name at definition time. It may also be made case insensitive. 

`define` tends to be slower that `const`, and will not benefit much from opcode cache. This will be specially visible when using large number of constants. 

It is recommended to use `const` whenever possible. 

## Rule Details

The following are considered a warning : 

```php
<?php

define('a', 1);
define('b', 'a' . 'c');
define('c', someClass::constant);

?>
```

The following are OK : 

```php
<?php

define('l', 3, true);
define('m', $x, true);
define('n', array(1,2,3), true); // before PHP 5.6

?>
```

## When Not To Use It
For backward compatibility, or to load configuration as constants, `define()` is still more convenient for definition. In terms of usage, both syntax are good.

## Further Reading

* [define() versus const (PHP Best practises)](https://phpbestpractices.org/#constants)
* [define vs const (Stackoverflow)](http://stackoverflow.com/questions/2447791/define-vs-const)

