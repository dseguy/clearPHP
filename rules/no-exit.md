<!-- Good Practices -->
# No Exit

It is possible to end the execution of a script with `die` and `exit` functions. They will interrupt the execution and destruct all resources. 

```php
<?php

if (mysql_connect('localhost', 'user', 'pass')) {
	die('No database');
}

?>
```

Exiting a script this way will also break any library that is including the `die` or `exit`. This may be difficult to spot, especially if those functions are used without any argument, thus displaying nothing about the location of the exit. 

Exiting is also bad in a destructor : any call to `exit` and `die` in a destructor will prevent the other destructors to be executed. 

It is usually better to `throw` an exception or raise an error (with `trigger_error`) or use any error handling set up available (returning a value, calling a `error` method, etc..). 

## Rule Details

The aim of this rule is to avoid using `exit` and `die` and rely on other error mecanisms. 

This is considered a warning. 

```php
<?php

exit();
exit(23);
exit("an error message");

exit; // no parenthesis

die(__METHOD__);

?>
```

This is considered legit. 

```php
<?php

// may be caught by error handler
trigger_error();

// may be caught by catch
throw new ExitException();

?>
```

## When Not To Use It
When the code is run as a commandline script, `exit` and `die` are good to return status, just like `return`. 

## Further Reading

* [Exceptions](http://php.net/manual/en/language.exceptions.php)
* [Trigger_error](http://php.net/manual/en/function.trigger-error.php)
* [Return](http://php.net/manual/en/function.return.php)
* [Understanding PHP objects](http://fr.slideshare.net/jpauli/understanding-php-objects)