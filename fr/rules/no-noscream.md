<!-- Good Practices -->
# No @

The `@` suppresses all local error displays. This practise has several drawbacks.

It may hide some legitimate errors : for example, when `fopen()` used to emit too many errors, the `@` would also hide errors such as missing file or unreadable file. 

Secondly, this operator will slow the code a lot. Compare the two codes below : the second one is much faster than the first. 

```php
<?php
// hidding errors
for($i = 0; $i < MAX; $i++) {
    @$y[$i]++;
}

// properly initializing 
for($i = 0; $i < MAX; $i++) {
    if (!isset($y[$i])) {
        $y = 1;
    } else {
        $y[$i]++;
    }
}
?>
```

Finally, it is not possible to activate or disable the operator without changing the code. Unlike `error_reporting()` which may be changed in the configuration file `php.ini`, `@` will stay in the code until removed. 

## Rule Details

The following code is considered a warning:

```php
<?php

$fp = @fopen('file.txt', 'r');
// No error will be reported

while($line = fgets($fp)) {
	process($line);
}

// incrementing $s without initializing it.
@$s++;

?>
```

<!--
## When Not To Use It
Never

-->
## Further Reading 

* [Example that shows the effect of scream](http://php.net/manual/en/scream.examples-simple.php)
* [ext/scream extension](http://pecl.php.net/package/scream)
