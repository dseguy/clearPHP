<!-- Good Practices -->
# No PHP4 Class Syntax

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

In PHP 5, constructors are now called `__construct` and if this function is not defined, if the class has no parent and if the method is not the last element of the current namespace, PHP will try to use the function that bear the class's name instead. This is meant to ensure backward compatibility. 

In PHP 4, properties were declared using the `var` keyword. This keyword is still available, and is a synonym of `public`. However, it should be replaced by `public` or another visibility. 

```php
<?php

// PHP 4 syntax
class foo {
	var $bar = 1;
}

// PHP 5 syntax
class bar {
	public $foor = 1;
}

?>
```

It is recommended to avoid PHP 4 class syntax, as it has been replaced by new and more powerful syntax. It may also be obsolete and dropped at some point in the future

## Rule Details

The following snippets are considered a warning:

```php
<?php

namespace {
	// rename this from PHP4_style to __construct()
	class PHP4_style {
		function PHP4_style() { /**/ } 
	}

	// rename this from PHP4_style to __construct()
	class PHP4_style_with_parent extends PHP4_style {
		// will use PHP4_style
	}

	// check PHP4_PHP5_hybrid and see if it may be dropped or renamed
	class PHP4_PHP5_hybrid {
		function __construct() { /**/ } 
		function PHP4_PHP5_hybrid() { /**/ } 
	}

	class oldStyleProperty{
		var $someProperty = 1;
	}
}



namespace Foo {
	class Bar {
   		public function Bar() {
       // treated as construct in PHP 5.3.0-5.3.2
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
	public $someProperty = 1;
	
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
