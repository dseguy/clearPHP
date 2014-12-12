<!-- Good Practices -->
# Useless Instructions

Useless instructions are valid instructions that don't provide anything useful. They are correctly compiled and processed but will not serve any purpose. 

They should be removed or completed so as to have impact in the code.


## Rule Details

This rule targets code that doesn't do anything useful. 

The following code is considered a warning:

```php
<?php
// literals in the code flow
1; 
My_CONSTANT;
$b;
function () { return $x = 3; }

// post-incrementation in a return
return $a++;

?>
```


The following pattern is considered legit:

```php
<?php

// properties may be processed with __get()
$object->property;

// pre-incrementation in a return
return ++$a;
?>
```

<!--
## When Not To Use It



## Further Reading

-->