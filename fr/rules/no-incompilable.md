<!-- Good Practices -->
# No Incompilable

Within an application, any PHP code should be compilable with the recommended version for the application : the recommended version is chosen by the application author. Compatible versions usually range a few middle version of PHP : a few versions backward, and a few versions forward. 

Newer version of PHP may introduce backward incompatibilities. Preparing the code for them means the code will have to be adapted or dropped. 

Older version of PHP may not support all the current version features. If backward compatibility is not important, support for such version will be dropped. This is normal behavior.

```php
<?php

mysql_connect($host, $user, $pass); // deprecated features in PHP 5.5

$y = [1, 2, 3]; // Array short syntax is introduced in PHP 5.4

?>
```
In the example above, the code is only compatible PHP 5.4 : `short syntax` is introduced in PHP 5.4, and such code won't be backward compatible with PHP 5.3. 
`mysql_connect` is part of ext/mysql, which is deprecated in PHP 5.5. This code will emit warnings and fatal errors in those versions, but will be fully compilable with PHP 5.4, the (possibly) recommended version. 

## Rule Details

This rule aims at avoid incompilable code. 

```php
<?php

// code incompatible with specific versions
mysql_connect($host, $user, $pass); // deprecated features in PHP 5.5
$y = [1, 2, 3]; // Array short syntax is introduced in PHP 5.4

// broken code
$y = ;
?>
```

## When Not To Use It
It should be always on for broken code. It may be used less aggressively if backward compatibility is not important. 

## Further Reading

* [PHP 5.6 backward incompatible changes](http://php.net/manual/en/migration56.incompatible.php)
* [PHP 5.5 backward incompatible changes](http://php.net/manual/en/migration55.incompatible.php)
* [PHP 5.4 backward incompatible changes](http://php.net/manual/en/migration54.incompatible.php)
* [PHP 5.3 backward incompatible changes](http://php.net/manual/en/migration53.incompatible.php)
* [PHP 5.2 backward incompatible changes](http://php.net/manual/en/migration52.incompatible.php)
n