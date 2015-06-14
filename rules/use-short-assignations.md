<!-- Performances -->
# Use Short Assignations

Some operators have a 'do-and-assign' version, that looks like a compacted version for = and the operator. 

```php
<?php
$x = $x + 2;
// may be written 
$x += 2;
?>
```

This approach is good for readability : it makes obvious that the variable is incremented with another value. This is typically very useful when data are collected in a variable until the variable is finally used, such as concatenations.

Short assignation makes better usage of memory. It will avoid copying the data to a new location, after allocation. This will save some memory. It may bring a speed boost if those lines are used intensively.

It is recommended to use the short assignation syntax all the time.

## Rule Details

This rule targets assignations that may be shortened. 

The list of short assignation is the following : 
* +=
* -=
* *=
* /=
* %=
* **=
* .=
* &=
* |=
* ^=
* >>=
* <<=

The following are considered a warning : 

```php
<?php

// + and * are commutable
$a = $a + $b;
$a = $b + $a;

// other operators cannot be swapped, so only one version may be adapted
$a = $a - $b;

// This may be shortened
$a = $a . $b . $c; 


?>
```

The following are OK : 

```php
<?php

// some operators cannot be swapped
$a = $b - $a; 

?>
```
<!--
## When Not To Use It
If the project doesn't use any OOP feature, it may ignore this rule.


## Further Reading

-->