<!-- PHP Manual -->
# No Unnecessary Concatenations

Concatenations double the amount of memory needed : it takes the original strings, and merge them into one, then, assign it to a variable or the output buffer. 

```php
<?php

echo 'a' . $b . 'c';

?>
```

In this example, two string literals and the variable `$b` are collected into one longer string, then echoed. 

In fact, `echo` do accept an unlimited number for arguments. It will display the values one after each other. So, the above code may be rewritten as : 

```php
<?php

echo 'a' , $b , 'c';

?>
```
At first, the difference is not obvious, as the concatenation operators dot `.` are simply turned into argument separators comma `,`. They also look alike very much. 

Behind the scene, since there is no concatenation, this expression will not cost more memory than what is currently used. 

On the other hand, the first version will start by building the concatenated string at the cost of `strlen($b) + 2` then display it. 

The gain will be significant if `$b` is big enough to have an impact. Short values, like integers, word-sized  or even sentence-sized strings will be painless. BLOB or TEXT from a database or TEXTAREA may be more impacting. 

`echo` will accept several arguments instead of concatenation. `print` will not accept more than one argument. Other functions that consumes big pieces of text, such as `file_put_contents` or `fwrite` will have to be checked.

```php
<?php

$text = file_get_contents('someFile.txt');

file_put_contents('newFile.txt', $text . "\n");

?>
```

This last concatenation will suddenly double the consumption of memory. 

Several alternatives of the above code will save that much memory : 

```php
<?php

// Good old fopen
$fp = fopen('no-concat.txt', 'w+');
fwrite($fp, $x);
fwrite($fp, "\n");
fclose($fp);

// Avoid concatenations and push to an Array()
$b = array($x, "\n");
$fp = fopen('no-concat.txt', 'w+');
foreach($b as $c) {
	fwrite($fp, $c);
}
fclose($fp);

// Even using a custom function will save memory
my_file_put_contents('no-concat.txt', $x, "\n");
function my_file_put_contents($filename, ...$text) {
    $fp = fopen('no-concat.txt', 'w+');
    foreach($text as $x) {
        fwrite($fp, $x);
    }
    fclose($fp);
}

?>
```
It is recommended to avoid useless concatenations anytime the volume of the manipulated data is significant (over a few kb)

## Rule Details

This rule is aimed at avoiding limiting the use of  concatenations when data gets large.

Check for methods that normally manipulate large amounts of data. 

Commands which needs to be complete before transmission, such as SQL queries, are not considered by this rule.

* file\_put\_contents
* fwrite
* stream_write
* socket_write
* print
* echo
* mail

The following patterns are considered warnings:

```php
<?php

echo $b. "\n";    // use ,
print "$c\n";     // use echo and ,

file_put_contents($file, $data . $more);
fwrite($filePointer, $data . $more);

?>
```
<!--
The following patterns are not considered warnings:

```php
<?php


?>
```


### Options

## When Not To Use It
If the equation is important to keep, then put it in a comment, and move this to documentation automatically. 

## Further Readings
-->

