<!-- Good Practices -->
# Commented Fallthrough

case in switch structures may be finalized using the `break` keyword. 

They may also continue in the next case, by letting the execution continue without `break`. This way, two case are merged in one. This is called fallthrough.

Fallthrough is usually rare. In the event they occur, most of them will be empty fallthrough, which are actually several case with the same name. 

Fallthrough are OK but needs to be commented so as to highlight their usage.

## Rule Details

This rule require that every `case` statement without a `break` has at least a comment. The following patterns are considered warnings:

```php
<?php
// case 'b' has uncommented fallthrough
switch (foo) {
    case 'a':
    case 'c':
        doSomethingForA();
        // will also do for c
        break 1;

    case 'b':
        doSomethingForB();

    default:
        doSomethingForDefault();
}
?>
```

The following code is considered legit : 


```php
<?php
// case 'b' has uncommented fallthrough
switch (foo) {
    case 'a':
    case 'c':
        doSomethingForA();
        // will also do for c
        break 1;

    case 'b':
        doSomethingForB();
        //also apply default behavior 

    default:
        doSomethingForDefault();
}
?>
```
<!--
### Options

## When Not To Use It

If default is not always necessary, you may disable this rule.
-->