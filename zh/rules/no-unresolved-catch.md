<!-- Good Practices -->
# Unresolved Catch

The `catch` instruction intercepts exceptions that are thrown inside the previous `try` block. 

```php
<?php

try {
	// do something
} catch (\ErrorException $e) {

} catch (\Unresolved\Exception $e) {

} catch (Exception $e) {

} catch (\Not\Even\An\Exception $e) {

} 

?>
```
In the examples above, the only safe code is the first `catch`. It uses an absolute namespaced class, that, indeed, exists. 

`catch` clauses will compare the expected class to the thrown exception : if the two matches, the block will be run. And if the `catch` exception doesn't exists, then it will never match a thrown exception, and will always fail. This is now dead code. 

The third one may exist, but is prone to innocent mistakes : when the current code is moved to a namespace, or if a namespace is added at the beginning of the code source, `Exception` will not resolve anymore to `\Exception` but to `\the\newNamespace\Exception`. Then, the situation will be the previous one. 

The fourth `catch`, uses a real class, but not one that is actually an `Exception`, or a sub-class of such. This means that an object of such class will never be thrown, since `throw` will check it to be an exception. And if no such exception is thrown, this `catch` is now dead code. 

It is recommended to make sure that the class used in the left part of the `catch` instruction is always valid.

## Rule Details

The following patterns are considered warnings:

```php
<?php

try {
	// do something
} catch (\ErrorException $e) {

} catch (\Unresolved\Exception $e) {

} catch (Exception $e) {

} catch (\Not\Even\An\Exception $e) {

} 

?>
```

<!--
### Options

## When Not To Use It
-->
## Further Readings
* [No Raw Exceptions](no-raw-exceptions.md)

