<!-- Good Practices -->
# Use Provided Constants

A large number of PHP functions accept options as argument. Often, though not always, the options are available as constants. For example, with `error_reporting` : 

```php
<?php

// Reporting Notice, errors and warnings.
error_reporting(E_ERROR | E_WARNING | E_PARSE | E_NOTICE);

// this is discouraged : similar to above but less readable
error_reporting(15);

// other example with one constant
get_html_translation_table (0);

// identical to 
get_html_translation_table (HTML_SPECIALCHARS);

?>
```

Using the constants makes the code more readable, and easier to maintain. 

It also prevent the code to decay as PHP evolve. For example, the following code as always been available and readable, even though the value of `E_ALL` has changed with PHP versions. 

```php
<?php

// Report all (available to all PHP versions)
error_reporting(E_ALL);

// Report all (available in PHP 4)
error_reporting(2047);

?>
```
It is recommended to always use the provided constants to configure such options. 

## Rule Details

Lots of native functions uses such arguments. Check the PHP manual for more information.

The following are considered a warning : 

```php
<?php

error_reporting(0);

http_build_query ($query_data, $numeric_prefix , $arg_separator, 1);

?>
```

The following pattern are considered OK :

```php
<?php

// using the right constante
error_reporting(E_NONE);

http_build_query ($query_data, $numeric_prefix , $arg_separator, PHP_QUERY_RFC3986);

// omitting the argument, so that it will use its default value
// no third parameter => default behavior (this behavior has no explicit constant)
stream_filter_append($stream, $filtername); 

?>
```
<!--
### Options
when static or self call will be different 

## When Not To Use It

If default is not always necessary, you may disable this rule.


## Further Reading
* 
-->