<!-- PHP Manual -->
# Use Smart Autoload

When it was introduced, class autoloading was build around the function `__autoload`. When this function is defined, PHP will use it to search for classes definitions if such a definition is missing. 

```php
<?php

// example of __autoload
function __autoload($classname) {
    $filename = PROJECT_ROOT.'/'. $classname .'.php';
    include($filename);
}

?>
```
This way, various libraries may cohabit peacefully. However, the function `__autoload` also introduces competition for libraries, that needed to provide their own support for the autoloading. 

Thus, `spl_autoload_register` was introduced : it allows the registration of autoloader methods, may it be functions, methods or static methods. They will be played one after each other, giving a chance to every library to have its own fitted autoloading. 

It is highly recommended to rely on `spl_autoload_register` and to avoid defining any `__autoload` function. 

## Rule Details

Any usage of `__autoload`  is forbidden. 

The following are considered warning : 
```php
<?php

// function definition
function __autoload($classname) {
    $filename = PROJECT_ROOT.'/'. $classname .'.php';
    if (file_exists($filename)) {
	    include($filename);
	}
}

?>
```

The following are considered legit : 

```php
<?php

// example adapted from the PHP documentation : 

// registering one's function
function my_autoloader($class) {
    $filename = PROJECT_ROOT.'/'. $classname .'.php';
    if (file_exists($filename)) {
	    include($filename);
	}
}

spl_autoload_register('my_autoloader');


// Or, using an anonymous function as of PHP 5.3.0
spl_autoload_register(function ($class) {
    $filename = PROJECT_ROOT.'/'. $classname .'.php';
    if (file_exists($filename)) {
	    include($filename);
	}
});

?>
```

## When Not To Use It
* If you need to include functions or constants, you can't use autoloading. 

## Further Reading
* [Autoloading Classes ¶](http://php.net/autoload)
* [spl\_autoload\_register](http://php.net/spl_autoload_register)
* [\_\_autoload](http://php.net/manual/en/function.autoload.php)
