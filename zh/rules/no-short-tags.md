<!-- PHP Manual -->
# No Short Tags

"PHP also allows for short open tag `<?` (which is discouraged since it is only available if enabled using the short_open_tag php.ini configuration file directive, or if PHP was configured with the --enable-short-tags option)."

## Rule Details

This rule require that every PHP opening tag is not a short tag. The following patterns are considered warnings:

```
<?
// ... some code
?>
```

The following code is considered legit : 

```
<?php


?>
```

```
<?= $y 
?>
```
<!--
### Options

## When Not To Use It

This is not checked by PHP but will lead to bugs.
-->

## Further Reading
* [PHP tags](http://php.net/manual/en/language.basic-syntax.phptags.php)
