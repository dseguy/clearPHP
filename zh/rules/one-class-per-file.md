<!-- Good Practices -->
# One Class Per File

One class per file makes it easy to find class definitions in the file system. It is confusing to search for class A in B.php file, as they are both in the same file. Version control log messages are also either to read.

It also help to follow PSR-0 to PSR-4 recommendations and automate class loading with namespaces and autoload. 

## Rule Details

This rule require that every `class` is defined in a file, and that every file that defines a class only hold one. The following patterns are considered warnings:

```php
<?php

class a { /**/ }

class b extends a { /**/ }

?>
```

The following code is considered legit : 

```php
<?php

class a { /**/ }
?>
```

Another file : 

```php
<?php

class b extends a { /**/ }

?>
```
<!--
### Options
-->
## When Not To Use It

If you have some mechanism that compile all classes into one file for faster loading, this rule may be ignore for that kind of file. 

