<!-- Good Practices -->
# Useless Unset

`Unset` is the function to use to destroy a variable. `unset` is also an operator `(operator)`, which actually does the same as the function. 

Unsetting variable have different effect, depending on the type of variable. The five following cases make it useless to unset a variable. 

* Unsetting a passed-by-value argument : arguments that are passed by value are copied from the calling context to the current one. Destroying the local variable is pointless : it will be destroyed (whatever that means), at the end of the method. 
* Unsetting a passed-by-reference argument : this time again, the actual value is left untouched. The reference itself is destroyed, but the value is still available in the original context. 
* Unsetting a global variable : inside a function, variable that are `global` can't be destroyed in the global scope by unsetting them. The only solution is to unset them in the `$GLOBALS` variable. 
* Unsetting a static variable : in a function, a static variable is a variable will survive the end of the current call, and be available in the next call. Unsetting the variable will simply destroy it in the current call : it will be recreated at the next call. 
* Unsetting a blind variable in a foreach loop : PHP works on a copy of the original array, and loops over the elements in that copy. Destroying such a variable, index or value, is useless. On the other hand, using the index to destroy the value in the original array is fine. 

Here is a pot-pourri of the previous situations : 

```php
<?php

function foo(&$argByReference, $argByValue) { 
	static $theStatic;
	global $theGlobal;
	
	unset($theStatic); // useless, will be back next call
	unset($theGLobal); // useless, should unset $GLOBALS['theGlobal'];
	unset($argByReference); // useless, will only destroy local reference
	unset($argByValue); // useless, will only destroy local copy 
	
	foreach($array as $key => $value) {
		unset($value);
	}
	
}

$varByReference = 1;
$varByValue = 2;
foo($varByReference, $varByValue);

?>
```

With a positive view, `unset` may be used to unset local variables in a function, global variables in the global scope, object properties and array index. 

It is recommended to avoid using unset on resilient variables.

## Rule Details

The following code is considered a warning:

```php
<?php

function foo(&$argByReference, $argByValue) { 
	static $theStatic;
	global $theGlobal;
	
	unset($theStatic); // useless, will be back next call
	unset($theGLobal); // useless, should unset $GLOBALS['theGlobal'];
	unset($argByReference); // useless, will only destroy local reference
	unset($argByValue); // useless, will only destroy local copy 
	
	foreach($array as $key => $value) {
		unset($value);
	}

}

$varByReference = 1;
$varByValue = 2;
foo($varByReference, $varByValue);

?>
```

The following pattern is considered legit:

```php
<?php

unset ($variableInGlobalScope);
unset ($GLOBALS['anyGlobalVariable']);

function foo() {
	$localVariable = array(1);
	
	unset($localVariable[0]);
	unset($localVariable);
	
	unset($this->property);
	
	foreach($array as $key => $value) {
		unset($array[$value]);
	}
}

?>
```

<!--
## When Not To Use It

-->

## Further Reading
* [unset](http://php.net/manual/en/function.unset.php)
