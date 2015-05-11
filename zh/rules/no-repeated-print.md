<!-- Performances -->
# No Repeated Print

Repeated calls to `print` or `echo`, should be merged into one call with concatenation. 

```php
<?php
	print "<!DOCTYPE html>\n";
	print "<html xmlns=\"http://www.w3.org/1999/xhtml\" lang=\"en\">\n";
	print "<head>\n";
	print "  <meta charset=\"utf-8\">\n";
	print "  <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\"> \n";
	print "  <title>Title</title>\n";
	/* ... */
?>
```

This should be written as : 

```php
<?php
	print "<!DOCTYPE html>\n".
	      "<html xmlns=\"http://www.w3.org/1999/xhtml\" lang=\"en\">\n".
	      "<head>\n".
	      "  <meta charset=\"utf-8\">\n".
	      "  <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\"> \n".
	      "  <title>Title</title>\n";
	/* ... */
?>
```

Generally speaking, it is recommended to accumulate all information in a variable, then output it with `echo` or `print` in one call rather than calling repeatedly those functions. 

It is also possible to put long blob of raw text in the HEREDOC or NOWDOC structures, or even in an external file. 

## Rule Details

The following pattern is considered warnings:

```php
<?php
	print "<!DOCTYPE html>\n";
	print "<html xmlns=\"http://www.w3.org/1999/xhtml\" lang=\"en\">\n";
	print "<head>\n";
	print "  <meta charset=\"utf-8\">\n";
	print "  <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\"> \n";
	print "  <title>$title</title>\n";
	/* ... */
?>
```

The following pattern are considered legit:

```php
<?php
	print "<!DOCTYPE html>\n".
	      "<html xmlns=\"http://www.w3.org/1999/xhtml\" lang=\"en\">\n".
	      "<head>\n".
	      "  <meta charset=\"utf-8\">\n".
	      "  <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\"> \n".
	      "  <title>Title</title>\n";
	/* ... */
?>
```

```php
<?php
	print <<<HTML
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>$title</title>
HTML;
	/* ... */
?>
```
<!--
### Options
## When Not To Use It

If needed, just use revert from the control version system. 

## Further Reading 

-->

