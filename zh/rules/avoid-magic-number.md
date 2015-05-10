<!-- Good Practices -->
# No Magic Number

Magic Number is a number that is written as a literal in the code, while it may have a special or related meaning that is not obvious to understand. 

At a later stage of the evolution, such magic number may need to be updated and a blind search/replace will not be possible as such literal may be used in other context.

```php
<?php

if (strlen($password) < 10) { // 10 is a magic number, that may change at any time. 
	$password['status'] = 33; // that is an error number, another magic number
	$password['checked'] += 1; // that is not a magic number : it only counts password's checks
}

?>
```

Magic numbers will raise problems when they appear in two different locations, and are updated only once. 

0, 1, 2 and 100 are often regarded as exceptions, as they are so often used. However, it is also a good idea to consider them as magic number and provide a better name for them : for example, 0 and 1 may be used and confused as `false` and `true`.

Magic numbers are useful in unit tests, where a wide range of valid and invalid values must be tested to check the behavior of the code.

It is recommended to provide explicit constant names for literals as often as possible. 0 and 1 should be considered too.

## Rule Details

This rules targets literals within comparisons, math expressions or assignations.

The following code is considered a warning:

```php
<?php
if ($value == 1) {  // magic number
	$value *= 1.206;   // magic number for VAT in some countries
}

if (3 > $value) { 
	// DoSomething()
}
?>
```

The following pattern is considered legit:

```php
<?php

$percentage /= 100; // classic percentage

$count += 1; // simple increment

?>
```

<!--
## When Not To Use It

-->

## Further Reading 

* [Magic number (programming)] (http://en.wikipedia.org/wiki/Magic_number_%28programming%29)
