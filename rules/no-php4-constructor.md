<!-- Coding Conventions -->
# No PHP4 Constructor

In PHP 4, constructors used be methods that bears the class's name. 

```php
<?php

class x {
	private $init = false;
	
	function x() {
		$this->init = true;
	}
}
?>
```

In PHP 5, constructors are now called `__constructor` and if this function is not defined, if the class has no parent and if the method is not the last element of the current namespace, PHP will try to use the function that bear the class's name instead. This is meant to ensure backward compatibility. 

## Rule Details

The following snippets are considered a warning:

```php
<?php

namespace {
	// rename this from PHP4_style to __constructor()
	class PHP4_style {
		function PHP4_style() { /**/ } 
	}

	// rename this from PHP4_style to __constructor()
	class PHP4_style_with_parent extends PHP4_style {
		// will use PHP4_style
	}

	// check PHP4_PHP5_hybrid and see if it may be dropped or renamed
	class PHP4_PHP5_hybrid {
		function __constructor() { /**/ } 
		function PHP4_PHP5_hybrid() { /**/ } 
	}
}

namespace Foo {
	class Bar {
   		public function Bar() {
       // treated as constructor in PHP 5.3.0-5.3.2
       // treated as regular method as of PHP 5.3.3
    	}
	}
}

?>
```


The following pattern is considered legit:

```php
<?php

class PHP5_style {
	function __construct() { /**/ } 
}


?>
```

<!--
## When Not To Use It
If you're still 
-->

## Further Reading 
* [] 
