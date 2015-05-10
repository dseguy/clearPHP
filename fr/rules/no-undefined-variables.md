<!-- Good Practices -->
# No Undefined Variables

There is no need to define a variable before using it in PHP. It will be created when used. However, using an undefined variable will lead to the emission of an error ('Undefined variable $x'), and its creation with a default value, depending on the context (0, false, null or empty string). This may lead to other errors. 

Some PHP functions will fill variables passed as argument without initializing them first (`proc_open`). Pass-by-reference arguments in custom functions may have the same effect. However, it may be good to initialize such variables first, so as to avoid unexpected situations, or simply to compare the result with the initial situation. 

It is recommended to always have a default value for variables. Checking for their existence before using them is also recommended. 


## Rule Details

This rules targets variables that are read or combined before being created with a default value. 

The following code is considered a warning:

```php
<?php

$aString .= 'a';

$anInteger++;

$anArray[] = 'b';

functionCall($undefinedVariable);

?>
```


The following pattern is considered legit:

```php
<?php

$aString = '';
$aString .= 'a';

$anInteger = 0;
$anInteger++;

$anArray = array();
$anArray[] = 'b';

$undefinedVariable = null;
functionCall($undefinedVariable);

?>
```

<!--
## When Not To Use It

## Further Reading 

* [PHP functions aliases] (http://php.net/manual/en/aliases.php)
-->