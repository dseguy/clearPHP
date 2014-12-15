<!-- Good Practices -->
# Avoid Globals

Global variables, in `PHP` as in other languages, allow to send a variable from one context to another. Global variables may be explicitely configure with `global` keyword, in functions, or, in the global scope, variables are automatically globals.

Global variables add coupling between apparently decoupled pieces of code : two classes may be in different namespaces and business logic, but when they share a global, they have a common point where they have to collaborate.

They cost memory, as `$GLOBALS` will grow with the number of global variables, and `$GLOBALS` is a super global, always available in every context. Besides, variables in the global scope are automatically considered as global, and may be access and manipulated as global in any function scope, even if the initial variable is not supposed to be global. 


```php
<?php
global $a; // explicit global variable
$a = 1;
$b = 2;

function c() {
	global $a, $b;
	
	$b = 3; $a = 4; // $a and $b are modified globally
}
?>
```

Using `global` keyword or `$GLOBALS` variable makes spotting global variables in a local context quite difficult. 


## Rule Details

This rule is aimed at preventing the use of global variables in the code.

The following codes are considered warnings:

```php
<?php
	global $a, $b;
	
	function b() {
		global $a;
		
		echo $GLOBALS['b'];

		/**/
	}
?>

## When Not To Use It

If avoiding global variables requires a lot of complex code, then it may worth using a few of them. But this is rare.

## Further Reading

* [Global Variables Are Bad](http://c2.com/cgi/wiki?GlobalVariablesAreBad)
* [Variables scope](http://php.net/manual/en/language.variables.scope.php)