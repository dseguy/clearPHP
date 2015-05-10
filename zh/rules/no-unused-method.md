<!-- Good Practices -->
# No Unused Methods

Methods that are created and not used anywhere in the code are most likely useless. Such methods consumes memory, use code space and may create confusion.

Methods may be use in the class, its children or in the rest of the code if the method is public. If the method is never found, it may be removed from the code, or marked as dead code.

## Rule Details

This rule is aimed at eliminating unused methods.

The following patterns are considered warnings:

```php
<?php

class foo {
	public function unusedMethod() {}
	
	public function usedMethod() {}
}

$bar = new foo();
$bar->usedMethod();

?>
```

<!--
### Options
-->
## When Not To Use It

If methods may be called dynamically in your code, you're likely to turn off this rule.
