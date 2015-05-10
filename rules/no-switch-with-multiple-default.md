<!-- Good Practices -->
# No Switch With Multiple Default

Switch statement may have several cases and one `default` statement, which will act as a catch-all for all unspecified cases. PHP compiles switches structures with several `default` cases, though only the first one is actually executed. 

All extra `default` cases are considered dead code, as they won't be executed. 

## Rule Details

This rule require that every `switch` statement has at least a `default` case. 

```php
<?php
switch (foo) {
    case 'a':
        doA();
        break 1;

    default:
        doDefault();
        break 1;

    case 'b':
        doB();
        break 1;

    default:
        doDefault();
        break 1;
}
?>
```

The following patterns are considered warnings:

```php
<?php
switch (foo) {
    case 'a':
        doSomething();
        break 1;

    case 'b':
        doSomething();
        break 1;

    default:
        doDefault();
        break 1;
}
?>
```
<!--
### Options

## When Not To Use It

If `default` is not always necessary, you may disable this rule.
-->