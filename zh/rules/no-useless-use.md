<!-- Good Practices -->
# No Useless Use

`use` statement are present at the beginning of the namespace to help PHP find classes definitions in the rest of the code. PHP will collect them and use them all to look for classes that are requested during the execution of the current file.

Any extra `use` statement will require extra searching to understand from which namespace the class will come, including resolving unnecessary name collisions. 

```php
<?php

namespace name {
	// foobar is useless
	use foo, bar, foobar;
	
	class barfoo extends foo implements bar {
	
	}
}

?>
```

It is recommended to keep the number of `use` statement to the minimum. 

## Rule Details

The following patterns are considered warnings:

```php
<?php

namespace name {
	// foobar is useless
	use foo, bar, foobar;
	
	class barfoo extends foo implements bar {
	
	}
}


?>
```

<!--
### Options

## When Not To Use It

-->
