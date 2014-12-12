<!-- Good Practices -->
# No Return Void

Returning is optional in `PHP`. When the interpreter reaches the end of the method, it simply `return null` by default. It is also possible to simply `return`, which will `return null`. 

However, it seems too bad that the return has been coded, and not the expected value. Most of the time, a boolean or a default value will be expected. It is recommended to explicitly `return null;` if nothing better is available.


## Rule Details

The following code is considered a warning:

```php
<?php

function method() {
	// ... more code
	return ;
}

?>
```


The following pattern is considered legit:

```php
<?php

function method() {
	// ... more code
	return null;
}

?>
```

<!--
## When Not To Use It



## Further Reading 

-->