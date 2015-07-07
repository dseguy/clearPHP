<!-- Good Practices -->
# Leave Last Closing Tag Out

PHP use `<?php` for opening a PHP sequence, and `?>` for closing it. Everything outside is considered as `raw HTML` and will be displayed as is, while everything inside is considered as PHP code.

```php
<?php

$a = 'a';

// This is not the last closing tag.
?>
B
<?php

echo $a;

// No closing tag, on purpose

```
The PHP interpreter will understand the end of the file as the end of the script, and will close any instruction. You may still get an fatal error if the instruction is badly build, or if there is not final `;`, so the behavior is the same as if you had closed the script.

The added value here is avoiding the infamous `Cannot modify header information - headers already sent by (output started at /path/to/file.php:lineNumber)` bug. This happens when there is raw HTML strings, which are immediately echoed to the server. Such strings are quite easy to spot when they are not blank (like a real `<html>` tag, or, when they are blank, at the beginning of the file.

At the end of the script, an extra space or tabulation might be difficult to spot, and, as such, will most probably generate the abovementioned error. This means that scripts must be checked, and may be commited again with whitespace fix. This is not efficient. 

It is recommended to leave the last PHP closing tag open, so as to avoid the infamous `Cannot modify header information - headers already sent by (output started at /path/to/file.php:lineNumber)`. 

## Rule Details

This rule is aimed at avoiding to use the last `?>` in a PHP script.

The following patterns are considered warnings:

```php
<?php

class myClass {
	/* some code */
}
?>
```

The following patterns are not considered warnings:

```php
<?php

class myClass {
	/* some code */
}

```

<!--
### Options
-->

## When Not To Use It
* If you hate unbalanced parenthesis or other unbalanced tags : [(](https://xkcd.com/859/)
* If you check all closing tags with your IDE or some code beautifier : just don't do this manually. 

## Further Readings
* [PHP Closing Tag](http://php.net/language.basic-syntax.phptags)
* [PSR-2 coding style guide](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)
