<!-- Good Practices -->
# Use Constant Rather Than Function

Some PHP functions has a constant counterpart. 


| Function  | Constant  | Description  |
|---|---|---|
| php_sapi_name  | PHP_SAPI  | Type of interface used  |
| phpversion  | PHP_VERSION  | Version of the current PHP  |
| php_ini_loaded_file  |   |   |


It is recommended to make sure the constant version, which is simply faster.

## Rule Details

The following patterns is considered a warning:

```php
<?php

if (php_sapi_name() == 'cli') {
	/**/
}

?>
```

The following patterns is considered valid :

```php
<?php

if (PHP_SAPI == 'cli') {
	/**/
}

?>
```
<!--
### Options

## When Not To Use It

## Further Readings
-->

