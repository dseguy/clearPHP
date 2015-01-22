<!-- Performances -->
# Echo With Commas

`echo` and `print` are the two functions used to display content to the standard output of PHP. This is used most of the time like this : 

```php
<?php

echo $someVariable . "\n";

print "$someVariable\n";

?>
```


One of their main differences is that `echo` accepts several arguments, while `print` only accepts one. This forces `print` to concatenate everything before outputing it, while `echo` will process all arguments one after each other. 


```php
<?php

// here, we use a  , comma, not a dot.
echo $someVariable , "\n";

print "$someVariable\n";

?>
```

The main consequence here is that `echo` will not concatenate the values before outputing : the values will be feed to the standard output one after each other. 

On the other hand, `print` will first concatenate everything. That concatenation will actually double the memory used, and provide no special effect here.

If `$someVariable` is small, both the memory and performance impact will be negligeable. When the size of the variable increase, more resources will be needed. 

It is recommended to always call `echo` with comma instead of concatenation. As for one-arguments calls, `print` and `echo` are the same. 


## Rule Details

The following code is considered a warning:

```php
<?php

// concatenation with "
echo "$a, $b, 'c', $d->e";

// concatenation with HEREDOC syntax
echo <<<HEREDOC
$a $b 'c' $d->e
HEREDOC;

// concatenation with .
print $a . $b . 'c' . $d->e;

?>
```

The following pattern is considered legit:

```php
<?php

// using commas and echo
echo $a, $b, 'c', $d->e;

// unique call
// avoid multiplying calls anyway

echo $someVariable;
echo "\n";

print $someVariable;

print <<<NOWDOC
some nowdoc block
NOWDOC;


?>
```

## When Not To Use It
If you're tired of `echo` versus `print` flamewars, or if the amount of data is small (< 100 kb)

<!--
## Further Reading 

* [Return] (http://php.net/manual/en/function.return.php)

-->