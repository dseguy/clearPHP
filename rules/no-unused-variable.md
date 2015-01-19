<!-- Good Practices -->
# No Unused Variables

Variables that are created and not used anywhere in the code are most likely useless. Such variables consumes memory, use code space and may create confusion.

As a simple check, any variable only used once in a context should be checked. 

Variables that are arguments are subject of a distinct rule, as their existence is under another set of constraints. See <a href="unused-arguments.md">Unused arguments</a>

## Rule Details

This rule is aimed at eliminating unused variables or arguments.

The following patterns are considered warnings:

```php
<?php
$x = 10; 
?>
```

The following patterns are not considered warnings:

```php
<?php
$x = 10;
$x++;
?>
```

<!--
### Options
-->
## When Not To Use It

If you don't want to be notified about unused variables, you can turn this rule off.
