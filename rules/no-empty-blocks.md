<!-- Good Practices -->
# No Empty Blocks

Some structures must have a following block, like a function definition or an `if then else` statement. When those are left empty, it leaves a confusing impression that something should be there but wasn't provided. 

```php
<?php

if (!file_exists('theFile.txt')) {

} else {
	print "Couldn't find the file\n";
}

function x() {

}

?>
```
Most of the time, code is expected and not finding it is confusing. Commenting such block is a good idea. Other alternative are to use it for default case, or set some basic behavior (logging an exception but not processing it further), leaving room for it to be updated later. 

It is recommended to avoid empty blocks in any situations. 

## Rule Details

The following patterns are considered warnings:

```php
<?php

// inverting the condition or setting a default case?
if ($condition) { } 
else {
	// doSomething
}

try {
	// doSomething
} catch (SomeException $e) { }
  finally { }

function y() { }

class Foo {
	// unless overwritten or overwritting
	function bar() { }
}

// Except for exceptions
class Foo extends Bar {}

while (fgets($fp, 10)) { }

?>
```
The following patterns are not considered warnings:

```php
<?php

class Foo extends Exceptions {

}

?>
```

<!--
### Options
-->
## When Not To Use It
When using empty blocks conflict with other rules (like never using negative conditions), this may lead to create empty blocks.

<!--
## Further Readings

-->
