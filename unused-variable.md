<!-- Best practices -->
# Disallow Unused Variables (unused-variable)

Variables that are created and not used anywhere in the code are most likely useless. Such variables consumes memory, use code space and may create confusion.

## Rule Details

This rule is aimed at eliminating unused variables or arguments.

The following patterns are considered warnings:

```php
$x = 10; 
```

By default, unused arguments cause warnings:

```php
function x ($foo) {
    return 5;
}
```

The following patterns are not considered warnings:

```php
$x = 10;
$x++;

```

<!--
### Options
-->
## When Not to Use It

If you don't want to be notified about unused variables or function arguments, you can safely turn this rule off.
