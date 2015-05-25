<!-- PHP Manual -->
# No Short Tags

PHP allows the short open tag `<?`, which is discouraged since it is only available if enabled using the `short_open_tag` `php.ini` configuration file directive, or if PHP was configured with the `--enable-short-tags` option).

Additionally the short open tag `<?` tries to interpret the XML doctype `<?xml` (and similar strings) as PHP code, but fails with `Parse error: parse error, unexpected T_STRING`.

## Rule Details

This rule requires that every PHP opening tag is not a short tag. The following patterns are considered warnings:

```
<? /* code */ ?>
```

The following code is considered legit:

```
<?php /* code */ ?>
```

```
<?= $text ?>
```
<!--
### Options

## When Not To Use It

This is not checked by PHP but will lead to bugs.
-->

## Further Reading

* [PHP tags](http://php.net/manual/en/language.basic-syntax.phptags.php)
